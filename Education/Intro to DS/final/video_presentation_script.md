# Video Presentation Script

Target length: 10-12 minutes, under the 15 minute limit.

## 0:00-0:45 - Opening

Introduce the project as an automatic osu!standard beatmap generator. State the core problem: given only song audio plus user controls such as BPM and difficulty, the system generates a playable `.osu` beatmap with circles, sliders, and spinners.

Show the GitHub repository link and mention that the paper focuses on the pre-diffusion encoder-decoder architecture, not the later latent/flow experiments.

## 0:45-2:00 - Motivation And Task

Explain that osu! mapping is hard because a good map needs rhythm alignment, readable spatial patterns, correct object types, and controlled difficulty. Emphasize that this is not just onset detection. The model has to output structured game objects with time, position, and type.

Show a short clip or screenshot of osu! gameplay or the generated Kaguya map in the editor.

## 2:00-3:15 - Data And Audio Features

Describe the dataset: community-created osu! beatmaps paired with audio from `project-riz/osu-beatmaps`.

Explain preprocessing:

- Audio is resampled to 22,050 Hz.
- Each window becomes 128 log-mel channels plus 1 onset-strength channel.
- Windows are 6 seconds long with 3-second stride.
- The target is the middle 3 seconds of each window.

Show `kaguya_mel_onset.png`. Point out that the spectrogram gives broad musical texture, while onset strength gives a rhythm-focused cue.

## 3:15-5:00 - Token Representation

Explain that the model predicts beatmap tokens instead of raw `.osu` text.

Cover the vocabulary:

- Special tokens
- Object type tokens
- Slider curve tokens
- 32 by 32 position grid tokens
- 128 beat-delta timing tokens

Emphasize the main representation finding: timing is modeled in beats, not raw milliseconds. A one-beat rhythm should be the same token at different BPMs.

Mention residual heads: the token gives a coarse time or position bin, and continuous residuals refine the exact timing, x, and y.

## 5:00-6:45 - Model Architecture

Show `encoder_decoder_architecture.png`.

Walk through the pipeline:

1. MP3 audio becomes 129-channel features.
2. AST receives the 128 mel channels.
3. A separate projection receives mel plus onset.
4. Onset gating injects onset-aware features into the AST representation.
5. Difficulty and BPM become a conditioning token.
6. A Transformer decoder generates tokens autoregressively.
7. Token and residual heads are converted back into `.osu` hit objects.

Make the key point: the previous working model was a real encoder-decoder Transformer, not diffusion. The architecture changed to latent/diffusion-style work at commit `cf8f590`; the best pre-diffusion state is `2b47831`, with `ae03d19` adding scrapbook notes.

## 6:45-8:15 - Training And Metrics

Describe the training loss:

`L_total = 0.8 * token cross entropy + 0.2 * residual Smooth L1`

Mention teacher forcing, curriculum learning, mixed precision, and WebDataset shards.

Show `pre_diffusion_metrics.png` and report:

- Timing MAE improved from 836.4 ms to 396.3 ms.
- Hit F1 improved from 0.0388 to 0.1082.
- Token edit distance improved from 0.8944 to 0.4357.

Explain that these numbers are better but still not human-quality. This honesty is important.

## 8:15-10:15 - Kaguya Generated Example

Show the generated Kaguya map video or editor playback.

Then show:

- `kaguya_generated_playfield.png`
- `kaguya_generated_timeline.png`
- `kaguya_generated_summary.png`

Say that the generated file contains 257 objects: 141 circles, 115 sliders, and 1 spinner over 86.34 seconds. The mean inter-object interval is 337.3 ms, and the mean jump distance is 138.9 pixels.

Interpret this carefully: the system generated a complete mixed-object chart, proving the pipeline worked end-to-end. But the output still had awkward timing, local repetition, and weak full-song structure.

## 10:15-11:30 - Limitations

List the main limitations:

- Six-second windows weaken global song structure.
- Autoregressive decoding accumulates errors.
- Sliders are fragile because they require multi-token grammar.
- Hit F1 remains low.
- Objective metrics do not fully capture playability or mapping style.
- The onset channel helped, but the zero-out diagnostic showed only modest influence.

## 11:30-12:30 - Future Work And Closing

Explain why the later architecture moved toward continuous representations, latent autoencoders, and flow matching. The motivation was not that the previous model was useless, but that its limitations pointed toward full-song continuous generation.

Close with the main finding: representation choices mattered. Beat-relative timing, onset features, per-channel normalization, and explicit conditioning made the model substantially better, even though the final generated maps were not yet polished.

End by showing the GitHub and final video links that will appear at the end of the paper abstract.

## Recording Checklist

- All group members appear on camera at least once.
- Keep screen sharing focused on figures, generated map playback, and metrics.
- Use one short Kaguya gameplay/editor clip.
- Keep the architecture explanation visual rather than code-heavy.
- Upload the final Zoom recording somewhere public.
- Put both `Code: \url{...}` and `Video: \url{...}` at the end of the abstract.
