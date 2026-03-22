# The Cunning Hare & The Lion — AR Storybook

An interactive AR folk tale (Panchatantra) built with **A-Frame + AR.js**.  
Works on **any mobile or desktop browser** — no app install needed.

## Quick Start (2 minutes)

### 1. Install VS Code + Live Server
- Download [VS Code](https://code.visualstudio.com/)
- Open VS Code → Extensions (Ctrl+Shift+X) → search **"Live Server"** → Install (by Ritwick Dey)

### 2. Run the project
- Open this folder in VS Code (`File → Open Folder`)
- Right-click `index.html` in the Explorer → **"Open with Live Server"**
- Your browser opens at `http://localhost:5500`
- **Allow camera access** when prompted

### 3. Print or display the Hiro marker
Open `assets/hiro-marker.html` in another browser tab/window and display it on screen, OR print it.  
Point your camera at it — the AR scene will appear instantly.

### 4. Interact
- **Tap the story panel** (bottom) to advance through all 5 scenes
- The marker can be on a phone screen, printed paper, or tablet
- Tap **"Retell the Story"** at the end to restart

---

## Mobile Testing (same Wi-Fi)

1. Open a terminal: `ipconfig` → find your IPv4 (e.g. `192.168.1.5`)
2. On your phone's browser: go to `http://192.168.1.5:5500`
3. Allow camera → point at Hiro marker → story begins

> **iOS Safari requires HTTPS.** Deploy to GitHub Pages (free) for iPhone testing.

## GitHub Pages Deployment (HTTPS / iOS)

```bash
git init
git add .
git commit -m "AR Hare and Lion storybook"
git remote add origin https://github.com/YOUR_USERNAME/ar-hare-lion.git
git push -u origin main
```
Then: GitHub repo → **Settings → Pages → Deploy from branch: main** → Save.  
Your HTTPS URL will be `https://YOUR_USERNAME.github.io/ar-hare-lion/`

---

## Project Structure

```
ar-hare-lion/
├── index.html          ← Main AR experience (all 5 scenes)
├── assets/
│   └── hiro-marker.html   ← Print or display this as your AR target
├── writeup.md          ← 1-page assignment write-up
└── README.md           ← This file
```

## Tech Stack

| Library | Version | Purpose |
|---|---|---|
| A-Frame | 1.4.0 | 3D/WebXR scene graph |
| AR.js | 3.4.5 | Marker tracking via webcam |
| Google Fonts (Cinzel + Lato) | — | Story typography |

All loaded via CDN — no `npm install`, no build step.

---

## The 5 Scenes

| # | Title | AR Characters |
|---|---|---|
| 1 | The Proud Lion | Lion rotates slowly at the river |
| 2 | The Cunning Hare Appears | Hare hops in beside the lion |
| 3 | Follow Me, O King | Both face the well in distance |
| 4 | The Reflection | Lion leans over well; reflection glows within |
| 5 | Wisdom Triumphs | Both bow; golden sparkles float upward |
