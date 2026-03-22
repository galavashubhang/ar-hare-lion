# AR Storytelling Write-Up
## The Cunning Hare & The Lion
**Shubhang Galava · March 2026**

---

## Tool / Framework Used

**A-Frame 1.4.0 + AR.js 3.4.5** — a fully web-based AR stack that runs directly in any modern mobile or desktop browser, with zero app installation.

- **A-Frame** is a declarative, HTML-first WebXR framework built on Three.js. 3D scenes are composed like HTML elements.
- **AR.js** extends A-Frame with real-world marker tracking using the device camera. I used the built-in **Hiro marker** (NFT-free, printable, works in under 1 second of detection).
- All characters are built from **A-Frame geometric primitives** (cylinders, spheres, tori, planes) — no 3D asset pipeline, no CORS, no loading failures.
- The story UI overlay is **vanilla HTML/CSS** (glassmorphism panels, Cinzel serif font, animated progress dots) layered over the AR canvas with `z-index` compositing.

---

## What I Built

A 5-scene interactive AR folk tale based on the Indian Panchatantra story *The Cunning Hare and the Lion*.

| Scene | Setting | Key Moment |
|---|---|---|
| 1 | Riverbank | Proud lion rotates slowly, surveying his domain |
| 2 | Forest path | Hare appears with a bouncing idle animation |
| 3 | Path to well | Both characters together; well visible in distance |
| 4 | The well | Lion leans over well; glowing reflection visible inside |
| 5 | Resolution | Both characters bow; golden sparkles float upward |

**Interaction model:** The user points their phone camera at a printed (or screen-displayed) Hiro marker. The scene anchors to the marker and persists as the user moves. Tapping the story panel at the bottom advances to the next scene with a smooth dark-flash transition. After the fifth scene an end card appears with the moral and a "Retell" button.

**Works on:** any Android/iOS browser (Chrome, Firefox, Safari via HTTPS/GitHub Pages), and desktop with a webcam.

---

## What I Would Do Differently With More Time

1. **Real 3D models** — Replace geometric primitives with rigged `.glb` character models from Sketchfab (CC0 license). A rigged lion with idle/roar/jump animations would make the emotional beats far more impactful.

2. **Surface detection (WebXR / ARCore)** — Switch from marker-based to surface-based AR so no printed marker is needed. Point at any flat surface and the story world appears.

3. **Spatialized audio** — Add ambient forest sounds in scene 1, water dripping in scene 4, and a triumphant cymbal in scene 5 using the A-Frame positional audio component.

4. **Particle systems** — The reflection scene would benefit from realistic water ripples; scene 5 from a golden particle burst. A-Frame's `aframe-particle-system` component makes this straightforward.

5. **Scene continuity** — Instead of snapping between discrete scenes, use GSAP/A-Frame `animation-mixer` to animate characters *transitioning* from one pose to the next, maintaining the spatial narrative.

---

## How I Would Extend This to a Full Multi-Scene Narrative System

```
NarrativeEngine
├── SceneGraph (JSON/YAML)           ← Scene definitions, character states, triggers
├── CharacterManager                 ← Loads GLB models, manages animations via Mixamo
├── TriggerSystem                    ← Tap | voice | gesture | gaze | proximity
├── TransitionDirector               ← Crossfade, wipe, cinematic cut, slow-mo
├── AudioDirector                    ← Spatial audio per scene, diegetic + non-diegetic
├── MarkerRouter                     ← Multiple markers = multiple story branches
└── ProgressPersistence              ← localStorage / Firebase for save states
```

The key insight is that an AR story should be a **directed graph**, not a linear list. Each scene node defines: *characters present*, *animations playing*, *trigger condition to advance*, and *possible next nodes*. This enables branching narratives ("does the lion learn his lesson or attack again?"), multi-user shared sessions (AR.js Networking), and creator tools where storytellers drag-and-drop node graphs to define folk tales without writing code — an AR story editor.

---

*Built in ~90 minutes using VS Code + Live Server + A-Frame + AR.js.*
*Hiro marker source: AR.js official documentation.*
