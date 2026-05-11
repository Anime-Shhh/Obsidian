# OsuMapper: Encoder-Decoder Beatmap Generation from Audio

## Abstract

This project explores automatic generation of osu!standard beatmaps from raw song audio. A beatmap is a time-aligned set of gameplay objects, such as circles, sliders, and spinners, that players interact with while listening to a song. Human-created maps require detailed rhythmic judgment, spatial pattern design, and difficulty balancing. The implemented system frames beatmap generation as a sequence-to-sequence learning problem: audio features are encoded by a pretrained Audio Spectrogram Transformer, and an autoregressive Transformer decoder generates a symbolic token sequence describing hit objects. The final pre-diffusion architecture uses 129-channel audio features, explicit BPM and difficulty conditioning, beat-relative timing tokens, onset-strength features, and hybrid discrete-continuous output heads. The system improved timing mean absolute error from approximately 836.4 ms to 396.3 ms and hit F1 from 0.0388 to 0.1082 compared with an earlier baseline. Although the generated maps were not yet human-quality, the project demonstrates that representation choices, especially beat-relative timing and onset-aware audio encoding, substantially affect neural beatmap generation.

## 1. Introduction

osu! is a rhythm game where players click, drag, and spin objects placed in time with music. In osu!standard mode, a beatmap specifies the exact timing and position of hit circles, sliders, and spinners. A strong beatmap is not just a set of clicks on beats. It must reflect musical structure, preserve readable spatial patterns, and match a desired difficulty level. Human mappers often spend many hours designing these maps.

The goal of this project is to automatically generate osu! beatmaps from audio. Given an MP3 file and user-specified controls such as difficulty and BPM, the model should output a playable `.osu` file. This is a challenging generative modeling problem because the output is structured in multiple ways. Timing must align with rhythm. Position must stay inside the playfield and form readable patterns. Object type must be chosen appropriately. Sliders require multiple control points. The final result must also feel coherent across the song.

The architecture described in this paper is the previous working version of the project before the later latent-space and flow-matching experiments. It used an encoder-decoder Transformer design. The encoder converted audio features into a sequence of embeddings. The decoder generated beatmap tokens autoregressively. The system was not subjectively good enough to replace human mapping, but it was complete: it loaded audio, generated tokens, decoded those tokens into hit objects, and produced valid `.osu` files. The Kaguya-sama inference run generated 257 hit objects from 29 audio windows.

The main lesson from the project is that better representation was more valuable than simply making the neural network larger. Early versions modeled timing in raw milliseconds and had weak rhythm awareness. The final pre-diffusion version used beat-relative timing, onset features, per-channel normalization, and explicit conditioning. These changes reduced timing error and improved hit F1.

## 2. Background

Beatmap generation can be viewed as conditional sequence generation. The condition is the song audio and difficulty target. The generated sequence is a structured description of gameplay objects. This resembles machine translation in the sense that the model translates one sequence-like input into another sequence-like output. However, the output is not natural language. It is a formal grammar of object types, times, coordinates, and slider parameters.

The project used spectrogram features instead of raw audio. A spectrogram represents audio over time and frequency. A mel spectrogram uses frequency bins based on human auditory perception. This is useful for music because low-frequency and high-frequency changes are represented in a perceptually meaningful way. The model used 128 mel bins.

The project also used onset strength. An onset is a moment where a new musical event begins, such as a drum hit, note attack, or sudden change in energy. osu! objects are often placed near onsets. A mel spectrogram contains enough information to infer onsets indirectly, but an explicit onset channel makes this cue easier for the model to access.

Transformers are sequence models based on attention. Self-attention lets a model compare all positions in a sequence. Cross-attention lets one sequence, such as generated beatmap tokens, attend to another sequence, such as encoded audio. The architecture used a pretrained Audio Spectrogram Transformer, or AST, as the audio encoder and a Transformer decoder as the beatmap generator.

## 3. Dataset and Preprocessing

The training data came from the `project-riz/osu-beatmaps` dataset. Each example contains audio paired with an osu! beatmap. During preprocessing, audio files were decoded, resampled to 22,050 Hz, converted to mono, and transformed into log-mel spectrograms. The preprocessing step also computed an onset-strength channel using audio onset detection.

The model input for one window was a tensor with 129 channels:

- 128 log-mel spectrogram channels
- 1 onset-strength channel

The system used overlapping audio windows. Each window was approximately 6 seconds long, and the stride was 3 seconds. The model predicted hit objects in the middle 3 seconds of the window. This gave the model local context before and after the region being mapped while keeping sequence length small enough for training.

The beatmap files were parsed into hit objects. Each object had a type, time, and position. Sliders additionally had curve type and control points. Spinners had a start and end time. These continuous objects were converted into a token sequence for training.

The preprocessed dataset was stored as WebDataset shards. This made it possible to stream many training examples efficiently on the school cluster and copy shards to node-local RAM disk for faster training.

![Kaguya-sama mel spectrogram and onset-strength feature](assets/kaguya_mel_onset.png)

## 4. Beatmap Tokenization

The model did not directly regress complete hit objects. Instead, it predicted a sequence of tokens. The vocabulary had 1,166 tokens:

| Token group | Count | Description |
|---|---:|---|
| Special tokens | 4 | Padding, beginning, ending, separator |
| Object type tokens | 6 | Circle, slider start/control/end, spinner start/end |
| Curve type tokens | 4 | Bezier, linear, perfect, Catmull |
| Position tokens | 1,024 | 32 by 32 grid over the 512 by 384 playfield |
| Beat timing tokens | 128 | Beat-delta bins at 1/16-beat resolution |

Circles used a compact three-token pattern:

```text
<beat_delta> <circle> <position>
```

Sliders used a longer grammar:

```text
<beat_delta> <slider_start> <start_position> <curve_type>
<slider_control> <control_position> ...
<slider_end> <end_position>
```

Spinners used timing and duration:

```text
<beat_delta> <spinner_start> <position> <duration_delta> <spinner_end>
```

This representation gave the decoder a language-like structure to learn. It could learn that a time token is often followed by an object type, that a circle is followed by a position, and that sliders have control points and an ending.

## 5. Beat-Relative Timing

One of the most important design changes was representing timing in beat space instead of raw milliseconds.

An earlier version of the project predicted time deltas in milliseconds. This is not musically ideal. The same rhythm has different millisecond durations at different tempos. For example, a one-beat gap is 500 ms at 120 BPM but about 345 ms at 174 BPM. If the model sees only milliseconds, it must relearn the same rhythmic idea for many tempos.

The final pre-diffusion model converted time deltas into beats:

```text
delta_beats = delta_ms / ms_per_beat
```

where:

```text
ms_per_beat = 60000 / BPM
```

The beat delta was quantized into 1/16-beat bins. At inference time, predicted beat deltas were converted back into milliseconds using the conditioned BPM.

This made the target more musical. The model learned concepts such as quarter-beat, half-beat, one-beat, and two-beat spacing. This change contributed heavily to the timing improvement.

## 6. Hybrid Discrete-Continuous Outputs

A purely discrete token representation would be too coarse for osu!. The playfield is 512 by 384 pixels, but the token grid was only 32 by 32. Each grid cell was 16 pixels wide and 12 pixels tall. If the model predicted only grid cells, object placement would be visibly imprecise.

To solve this, the model used hybrid outputs. The decoder predicted both discrete tokens and continuous residual values. A position token selected the coarse grid cell. The x and y residual heads predicted small offsets inside that cell. A beat token selected the coarse rhythmic bin. The time residual head predicted a small offset inside that bin.

This approach gave the model the benefits of both classification and regression. Classification handled the large structured decision of which token should appear next. Regression refined the exact timing and position.

## 7. Model Architecture

The model had three conceptual parts:

1. Audio encoder
2. Conditioning encoder
3. Beatmap decoder

The audio encoder used a pretrained AST model. AST is a Transformer model trained on audio spectrograms. Using AST allowed the project to benefit from learned audio representations instead of learning audio perception entirely from scratch.

AST expects 128 mel channels. The project had 129 channels because it added onset strength. The solution was a two-path encoder. AST received only the 128 mel channels. A separate linear projection received all 129 channels. The projected features included onset information, so they preserved the rhythm cue that AST would otherwise not see.

The model then used onset gating. The projected 129-channel features were aligned to AST's output length and passed through a learned sigmoid gate. The gated projection was added to the AST output:

```text
encoder_out = ast_out + gate * projected_features
```

This let the model decide how much of the onset-aware projection to inject at each time step. It also preserved the benefit of pretrained AST features.

The conditioning encoder handled difficulty and BPM. Difficulty was mapped to one of five bins: Easy, Normal, Hard, Insane, or Expert. The difficulty bin was embedded with a learned embedding table. BPM was log-scaled and passed through a small MLP. The difficulty and BPM representations were combined into one conditioning token.

The beatmap decoder was an autoregressive Transformer decoder. It generated one token at a time. It used causal self-attention over previous beatmap tokens and cross-attention over the conditioning token plus audio encoder output. The decoder had token embeddings, positional embeddings, 6 decoder layers, 8 attention heads, model width 768, and feedforward width 2048.

The decoder output passed into four heads:

- A discrete token head
- A time residual head
- An x residual head
- A y residual head

This is the core encoder-decoder architecture of the pre-diffusion model.

![Pre-diffusion OsuMapper encoder-decoder architecture](assets/encoder_decoder_architecture.png)

## 8. Training Method

The training objective combined token prediction and residual regression:

```text
L_total = 0.8 * L_discrete + 0.2 * L_residual
```

`L_discrete` was cross-entropy over the 1,166-token vocabulary. `L_residual` was Smooth L1 loss over time, x, and y residual values. Padding tokens were ignored.

The model used teacher forcing during training. In teacher forcing, the decoder receives the correct previous token while learning to predict the next token. This makes training more stable. The teacher forcing ratio decayed over time so the model gradually had to rely more on its own predictions.

Training also used curriculum learning. Early training focused on simpler circle-only examples. Later phases introduced sliders and then full maps. This helped because sliders require longer and more fragile token sequences than circles.

The system was trained on SLURM-managed GPUs. It used mixed precision, gradient clipping, AdamW optimization, cosine learning-rate scheduling, and WebDataset data loading. Shards were copied to `/dev/shm` at job start to reduce I/O overhead.

## 9. Inference Pipeline

Inference converted a song into a complete `.osu` file.

First, the MP3 was loaded and resampled. The user could provide BPM, or the system could estimate it. The user also provided a target difficulty. The song was split into overlapping 6-second windows. For each window, the model computed mel and onset features, normalized them, and generated a token sequence autoregressively.

The generated tokens were detokenized into hit objects. Beat deltas were converted back to milliseconds with the provided BPM. Position bins and residuals were converted back into playfield coordinates. The objects from all windows were merged into global song time. Finally, overlapping duplicate objects were removed and the `.osu` file was written.

The Kaguya-sama inference run used this pipeline. The log indicates that the model loaded `/common/users/asj102/osu_project/models/best.pt`, used BPM 138.0 and difficulty 4.0, processed 29 windows, and generated 257 hit objects. This generated map is useful as a qualitative example, even though it was not subjectively human-quality.

## 10. Results

The project tracked validation loss, edit distance, timing MAE, hit F1, and onset influence.

Validation loss measured next-token prediction quality under teacher forcing. Edit distance measured token-sequence similarity. Timing MAE measured absolute timing error after converting tokens back into hit-object times. Hit F1 measured whether predicted objects matched ground truth objects in both time and position.

The earlier baseline had:

| Metric | Value |
|---|---:|
| Train loss | 1.5598 |
| Validation loss | 2.2213 |
| Edit distance | 0.8944 |
| Timing MAE | 836.4 ms |
| Hit F1 | 0.0388 |

The final pre-diffusion encoder-decoder model had:

| Metric | Value |
|---|---:|
| Train loss | 1.7170 |
| Validation loss | 2.1072 |
| Edit distance | 0.4357 |
| Timing MAE | 396.3 ms |
| Hit F1 | 0.1082 |

The timing MAE improved by roughly 2.1x, and hit F1 improved by roughly 2.8x. Edit distance also improved substantially. These changes show that the model became better at predicting structured beatmap sequences and aligning hits to the song.

![Pre-diffusion metric improvements](assets/pre_diffusion_metrics.png)

However, the absolute metrics still show the model was not solved. A timing error of 396 ms is still large for rhythm-game playability. A hit F1 of 0.1082 means many generated objects did not match the ground truth under the metric's time and position thresholds. The model learned meaningful structure but did not reach professional mapping quality.

## 11. Qualitative Findings

The generated Kaguya map is important because it shows the full system working end-to-end. The model produced a `.osu` map rather than just loss numbers. The output had hundreds of objects distributed across the song. This means the model learned to produce valid object syntax and non-empty gameplay content.

The local generated file contains 257 hit objects over an 86.34 second span: 141 circles, 115 sliders, and 1 spinner. The mean inter-object interval is 337.3 ms, with a median of 221.5 ms. The mean spatial jump distance between consecutive objects is 138.9 pixels, with a median of 126.1 pixels. These statistics show that the model generated more than isolated clicks: it produced a dense mixed-object chart with nontrivial spatial movement. They also provide a concrete way to discuss why the output was only partially successful. Density and object diversity are present, but timing and pattern quality still need human-level structure.

![Generated Kaguya playfield object path](assets/kaguya_generated_playfield.png)

![Generated Kaguya object timeline and density](assets/kaguya_generated_timeline.png)

![Generated Kaguya object summary](assets/kaguya_generated_summary.png)

At the same time, subjective quality was limited. The old architecture could produce awkward timing, repeated patterns, and weak long-range structure. These issues are expected from a short-window autoregressive model. Each 6-second window is generated mostly independently, so the model does not have a strong understanding of sections, phrases, choruses, or overall difficulty pacing.

The onset zero-out diagnostic also showed that the onset channel had only modest influence. The final logit difference was 0.0049. This is better than completely ignoring onset, but it suggests the model still relied heavily on broad spectrogram features and token priors.

## 12. Discussion

The most important result is that representation improvements directly improved objective metrics. Beat-relative timing changed the problem from predicting arbitrary millisecond values to predicting musical subdivisions. Onset strength gave the model explicit rhythmic evidence. Per-channel normalization made sure the onset channel was numerically visible. Difficulty and BPM conditioning let the model separate user control from generated content.

This architecture also shows the strength and weakness of autoregressive token models. Token sequences are natural for representing structured objects. They make it possible to model circles, sliders, spinners, curve types, positions, and durations using one decoder. But autoregressive decoding accumulates errors. If the model predicts a bad token early, later predictions can be affected. Also, local windows make full-song coherence difficult.

The model's validation loss was not a perfect proxy for playability. A model can achieve reasonable token loss while still producing maps with poor rhythm or spacing. Timing MAE and hit F1 are more directly related to map quality, but even they do not capture everything human players care about. A generated map can match object count and timing while still feeling awkward because of patterning, spacing, or slider design.

## 13. Limitations

The largest limitation was global coherence. The model generated local windows, not full songs. Human mappers think in phrases, repeated motifs, contrast between sections, and difficulty progression. A 6-second model cannot fully represent this.

The second limitation was autoregressive error accumulation. The decoder generated one token at a time, so mistakes could compound. This was especially problematic for sliders because sliders require several tokens to form one object.

The third limitation was objective evaluation. Hit F1 and timing MAE are useful, but they are not the same as human playtesting. A model can score better while still producing maps that feel unnatural.

The fourth limitation was onset influence. The project improved onset handling, but the diagnostic showed the model did not depend on onset as strongly as desired.

Finally, the model inherited noise from community-created beatmaps. Human maps vary widely in quality, style, metadata correctness, and difficulty labeling. This makes supervised learning harder.

## 14. Future Work

The next architectural direction is to move away from pure autoregressive token generation. A continuous signal representation can model beatmaps as dense time-series channels over the whole song. A latent autoencoder can compress this signal into a structured representation of playable chart behavior. A flow-matching model can then generate or refine latents conditioned on audio and difficulty.

This future direction addresses the main limitations of the old architecture. Full-song latent generation can improve global coherence. Continuous signals can represent cursor motion, sustain, slider progress, and density more naturally than token sequences. Flow matching can generate maps with fewer iterative steps than classic diffusion.

Other useful improvements include stronger density conditioning, beat-phase features, phrase-level conditioning, ranked-only data filtering, and human playtest evaluation.

## 15. Conclusion

The pre-diffusion OsuMapper architecture demonstrated a complete end-to-end neural beatmap generator. It converted raw audio into mel and onset features, encoded those features with a pretrained AST-based encoder, and generated beatmap tokens with an autoregressive Transformer decoder. It used explicit BPM and difficulty conditioning, beat-relative timing, and hybrid discrete-continuous output heads.

The model was not yet good enough to create polished human-quality maps, but it produced measurable progress. Timing MAE improved from approximately 836.4 ms to 396.3 ms, and hit F1 improved from 0.0388 to 0.1082. The Kaguya-sama example showed that the system could generate a complete `.osu` map from an MP3.

The main lesson is that musical representation matters. Beat-relative timing, onset strength, and explicit conditioning made the learning problem more aligned with the structure of rhythm-game mapping. These findings justify the later move toward continuous full-song representations and latent flow matching.
