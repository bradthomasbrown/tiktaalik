a fundamental part of our approach to things is to "navigate the abstract space" for which we currently have two "modes of transportation":
- abstraction
- modularization

In abstraction, we ask "what is the category this thing falls under", where the category is the abstraction.

In modularization, we ask "if this is a category, what things are components of it", where the components are the modules.

functional programming can be thought of to just be more modular programming

we may computationally modularize things, with an extreme example being this:

| **From \ To**           | **A (Math)** | **B (Binary)** | **C (IPA)**    | **D (Ortho)**  | **E (Mel-Spectrogram)**  | **F (Prosody)**    | **G (Emotion)** |
| ----------------------- | ------------ | -------------- | -------------- | -------------- | ------------------------ | ------------------ | --------------- |
| **A (Math)**            |              |                |                |                |                          |                    |                 |
| **B (Binary)**          |              |                | **BC** (B → C) |                |                          |                    |                 |
| **C (IPA)**             |              | **CB** (C → B) |                | **CD** (C → D) | **CE** (C → E)           | **CF** (C → F)     |                 |
| **D (Ortho)**           |              |                | **DC** (D → C) |                | **DE** (D → E via C → E) | **DF** (D → C → F) | **DG** (D → G)  |
| **E (Mel-Spectrogram)** |              |                |                |                |                          | **EF** (E → F)     | **EG** (E → G)  |
| **F (Prosody)**         |              |                |                |                |                          |                    |                 |
| **G (Emotion)**         |              |                |                |                |                          |                    |                 |

What this is, roughly, is a table of different things where we may view the things as either inputs or outputs to theoretical machines.
DE(d) can be thought of as a machine that converts text to speech (orthography to mel-spectrograms), but we may then also consider conversions between other formats and things, like IPA strings or pure binary values.

We've had the concept to create new terms that functioned as abstractions of existing terms, which, when coupled with some expansion of the term into "familiar existing terms" could be delivered to a person or LLM as an "extension of the current language". 