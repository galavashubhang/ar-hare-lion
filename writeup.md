# The Cunning Hare & The Lion — Panchatantra AR Experience
**Shubhang Galagali · March 2026**

---

### Framework Used: A-Frame + AR.js

Given a two-day constraint and zero prior AR experience, the decisive factor for me was time-to-working-prototype. Unity + Vuforia requires a full IDE, SDK setup, build pipeline — easily a day of setup alone. ARCore is Android-exclusive and requires Android Studio. 8th Wall is paid. A-Frame 1.4.0 + AR.js 3.4.5 was the only stack that could go from zero to a working, camera-enabled AR experience in a browser tab within hours using only an HTML file served over HTTPS. It runs on any modern Android or iOS browser, works on desktop with a webcam, and deploying to GitHub Pages provided the HTTPS endpoint needed for camera access on mobile. For a rapid prototype proving an AR storytelling concept, this was the correct and efficient choice.

---

### What I Built

A five-scene interactive AR folk tale based on the Panchatantra story of The Cunning Hare and Lion (Bhasuraka). Pointing a phone camera at a Hiro marker (or a laptop screen displaying it) triggers a scene anchored to the marker. All 3D characters — a golden lion, a grey hare with pink ears, and a stone well — are built from A-Frame geometric primitives (cylinders, spheres, tori, planes) with layered animations: lion with a mane, a wagging tail (seen clearly in scene 1); the hare hops with forward body-tilt; the well has a pulsing water surface and expanding ripple circle; and the final scene shows the drowned lion lying flat in a blue water pool while the hare spins victoriously. A glassmorphism HTML overlay provides story text, animated progress dots, and a dark-flash scene transition. Tapping the story panel advances scenes; a 5-second delay after the final scene reveals the moral card. The experience is fully deployed at https://galavashubhang.github.io/ar-hare-lion/.

---

### What I Would Do Differently With More Time

I have written the code for this prototype with the assistance of Claude Sonnet 4.5 (Anthropic), used as a pair-programming tool to finish this assignment under the time constraint. Depending on how much LLM usage is desired or permitted in future work, I would invest time in writing the code independently to deepen understanding of the A-Frame component system and Three.js internals. On the technical side, I would replace geometric primitives with properly rigged .glb character models from Sketchfab (CC0 license) for idle, walk, and action animations — the difference in expressiveness is significant. The Hiro marker is a real constraint on mobile: to use it, you must print it, lay it flat on a surface, and view it from a specific angle — this is impractical for casual users on phones. I would switch to WebXR surface detection so the story anchors to any flat surface without a printed target (I need to read more on how to implement this). I would also optimise the story and pacing for the intended audience — for example children (ages 6–10), scenes need shorter text, larger visual cues, and audio narration; for older students, richer dialogue and moral discussion prompts make more sense. These are system design decisions that should precede any implementation.

---

### How I Would Extend This to a Full Multi-Scene Narrative System

A production AR folk-tale system should be architected as a directed scene graph, not a linear array. Each scene node would define: characters present and their animation states, the trigger condition to advance (tap, voice command, gaze dwell, or proximity), possible next nodes (enabling branching narratives — "does the lion learn, or grow angrier?"), and associated spatial audio tracks. A TransitionDirector would handle cinematic cuts, crossfades, or slow-motion effects between scenes; and a NarrativeEngine would read scene definitions from a JSON/YAML file, making the system story-agnostic — any folk tale could be authored without touching code. The ultimate extension is a no-code story editor: a drag-and-drop node graph where educators or storytellers define scenes, characters, and branches visually — turning the system from a single AR experience into a platform for interactive folk-tale authoring.
