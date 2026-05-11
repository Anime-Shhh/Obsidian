# Intro to Data Science Final Presentation Script: Osu! Beatmap Generator

**Target Time:** 9 - 10 minutes (Approx. 1 minute per slide)
**Speakers:** Ashwath & Animesh

---

## Slide 1: Opening
**[Ashwath]**
Hello everyone, welcome to our presentation. My name is Ashwath, and this is my partner Animesh. Today, we're going to be talking about our final project: An Automatic Beatmap Generator for the rhythm game, osu! 

To put it simply, our goal was to build an AI system where you can give it an MP3 file of a song, tell it how hard you want the game to be, and it will automatically generate a fully playable, fully designed level for you to play. 

---

## Slide 2: Motivation And Task
**[Animesh]**
*([Play the osu! video on the slide])*

For those who might not be familiar with it, the video playing behind me shows what osu! looks like. It is a highly competitive rhythm game where players use their mouse or tablet to click, drag, and spin objects on the screen perfectly in time with the music. 

The levels you play on are called "beatmaps". Currently, almost all beatmaps are created manually by humans. Mappers spend dozens, sometimes hundreds of hours carefully placing objects so they sync with the beat, form readable patterns on the screen, and progress naturally in difficulty. 

Our task was to automate this. And this is actually a really hard problem. It’s not just "onset detection"—which is just finding out *when* a drum beat happens. The model actually has to output structured game objects: it has to decide *when* an object appears, *where* on the 512-by-384 pixel screen it should go, and *what type* of object it should be—a quick tap circle, a long slider, or a fast spinner. 

---

## Slide 3: Data And Audio Features
**[Animesh]**
*([Point to the code screenshot on the slide])*

To train an AI to do this, we used a dataset of thousands of community-created beatmaps paired with their audio files. On this slide, you can see a snippet of the code we just added. An `.osu` file is basically just a structured text file. At the bottom, you can see the "HitObjects" section—these are just X and Y coordinates and timestamps in milliseconds. 

Now, how does the AI actually *listen* to the song to generate this code? We don't just feed it raw audio files. Instead, we chop the audio into 6-second windows and transform the audio into two special features:

First is a **Mel Spectrogram**. Think of this as a visual picture or a heat-map of the audio. It shows the frequencies and pitch over time, specifically scaled to how human ears perceive sound. This gives the AI the broad musical texture of the song.

Second is **Onset Strength**. An "onset" is a sudden burst of energy in a song—like a snare drum hit or a sudden vocal spike. By giving the AI a dedicated channel just for these bursts, it makes it much easier for the model to know exactly *when* a beat is happening so it can place an object there.

---

## Slide 4: Token Representation
**[Ashwath]**
So, Animesh just explained how the AI hears the music. But how does it output the game level? 

If we just asked the AI to write the raw text file you saw on the last slide, it would make a lot of typos. Instead, we turned the game objects into a vocabulary of "Tokens"—kind of like teaching the AI a new language. 

Our vocabulary has things like "Object Type" tokens, "Position Grid" tokens, and "Timing" tokens. 

The biggest breakthrough we had here was how we handled time. Originally, we asked the AI to guess the timing in raw milliseconds. But mathematically, a half-second gap at a slow tempo means something completely different than a half-second gap at a fast tempo. The AI was getting confused. So, we changed the system to model time in **beats**. Now, a one-beat gap is always a one-beat gap, regardless of the song's BPM. This made the AI learn rhythm much faster. 

Finally, the tokens just pick a general grid square on the screen. To make it pixel-perfect, we use something called "residual heads," which are just fine-tuning tools that nudge the object slightly so it lines up perfectly.

---

## Slide 5: Model Architecture
**[Animesh]**
Here is a look at the actual brain of our system: an Encoder-Decoder model.

Here’s the step-by-step pipeline: The MP3 audio comes in, and is converted into the 129 channels of Mel Spectrogram and Onset data I mentioned earlier. 

This data is fed into an **AST**, which stands for Audio Spectrogram Transformer. A Transformer is the same type of AI architecture that powers ChatGPT, but an AST is specifically pre-trained to understand pictures of audio. 

We feed the AST the broad musical texture, but we also explicitly inject that "Onset" or drum-hit data into it so it doesn't lose the rhythm. We also give it a token that tells it the desired difficulty and BPM.

Finally, all of this understanding gets passed to the "Decoder". The Decoder's job is to read all that music data and then write out our Beatmap tokens one-by-one, autoregressively—meaning it guesses the first token, looks at what it just wrote, and then guesses the second token, over and over until the map is done.

---

## Slide 6: Training And Metrics
**[Ashwath]**
So, how did it actually perform?

We trained the model by having it guess the next token in the sequence, and penalizing it when it guessed differently than the human mappers in our dataset. 

Our metrics saw massive improvements after we implemented the beat-relative timing and onset features. 
- Our **Timing Error**—which measures how many milliseconds off our object was from a human's object—dropped from over 836 milliseconds down to 396 milliseconds. It got more than twice as accurate!
- Our **Hit F1 score**—which measures if we placed the correct object at the correct time and place—jumped from about 3.8% to 10.8%. 

Now, to be completely honest about our results: while the model got drastically better, 400 milliseconds of error is still too laggy to be comfortably playable in a fast-paced game like osu!. The metrics prove the AI is learning the structure, but it's not quite at a human-level mapping quality yet.

---

## Slide 7: Kaguya Generated Example
**[Ashwath]**
To prove our pipeline actually worked end-to-end, we ran the opening theme song of the anime "Kaguya-sama: Love is War" through our model.

The AI successfully generated a complete, valid .osu file! Over an 86-second span, it created 257 objects: 141 circles, 115 sliders, and 1 spinner. 

If you look at the playfield diagram on the slide, you can see that the model didn't just place objects randomly or stack them all in the center. It actually moved across the screen, creating jumps that averaged about 138 pixels in distance. 

However, playing it reveals some flaws: the timing can feel awkward, and it tends to repeat local patterns rather than building a cohesive, flowing structure for the whole song. 

---

## Slide 8: Limitations
**[Animesh]**
And that leads us into our limitations. Why didn't it map perfectly?

First, because we fed the audio in 6-second windows, the model couldn't see the "big picture." Human mappers map choruses differently than verses, but our AI didn't know what part of the song it was in. 

Second, because our Decoder is "autoregressive" and generates tokens one-by-one, errors accumulate. If it places one object at the wrong time, all the objects after it will also be off-beat.

Finally, "Sliders" in the game are very fragile. A slider requires a start point, a specific curve type, and an end point. Generating all of these tokens perfectly in a row is really hard for a step-by-step generator to do without messing up.

---

## Slide 9: Future Work And Closing
**[Animesh]**
So, where does the project go from here? 

To solve these limitations, the next step in our architecture is to move away from guessing tokens one-by-one, and instead move towards **Continuous Representations and Flow Matching**. In simple terms, instead of typing out a level like a sentence, the AI would generate the entire song's level all at once as a continuous wave. This helps the AI understand the global structure of the song and prevents step-by-step errors from piling up.

In conclusion, the biggest takeaway from our project was that **representation matters**. By tweaking how we represented time—changing it to beats instead of milliseconds—and explicitly showing the model sudden bursts of sound, our AI became dramatically better at generating rhythm game levels. 

Thank you so much for listening. We have our GitHub repository linked here, and we'd be happy to take any questions!
