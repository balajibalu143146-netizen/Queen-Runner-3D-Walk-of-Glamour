# 👑 Queen Runner 3D: Walk of Glamour

A full-featured, mobile-friendly 3D hyper-casual runner game built with **Babylon.js** and WebGL. Strut down the royal palace runway, make chic fashion choices at dual archway gates, collect golden spinning coins, dodge mud puddles, level up your glamour tier, and undergo the ultimate **Majestic Queen Transformation** atop the Coronation Throne!

---

## ✨ Features Included

- 🎮 **Real 3D WebGL Gameplay**: Powered by Babylon.js with hardware-accelerated 60 FPS rendering.
- 👸 **Animated 3D Runner Character**: Stylized hierarchical skeletal rig with head, hair, torso, flowing dresses, heels, and accessories.
- 🏃 **Catwalk Running Animation**: Procedural catwalk swagger with sensual hip sway, dynamic leg swing, knee flex, rhythmic arm pump, and responsive banking tilt into turns.
- 🛣️ **3D Royal Runway Environment**: Elevated polished marble runway with a plush velvet red carpet runner, glowing neon borders, and golden guide rails.
- 🌳 **Rich Royal Scenery**: Fairytale castle spires, blooming cherry blossom (sakura) trees, trimmed topiary hedges, milestone archways, and cheering paparazzi camera flashes!
- 🚪 **3D Fashion Choice Gates**: Dual archways with procedural dynamic textures, glowing curtains, high-contrast rewards/penalties, and moving oscillating gates in later levels.
- 💰 **Spinning 3D Golden Coins & Gems**: Floating coins with embossed stars, royal ruby/cyan gems, and smooth magnetism suction towards the runner.
- 👗 **5 Progressive Outfit States**:
  1. *Tier 1 (Casual / Slouch)*: Baggy hoodie, faded pants, messy bun.
  2. *Tier 2 (Street Chic)*: Pastel crop top, trendy skirt, chic bob haircut.
  3. *Tier 3 (Gala Diva)*: Shimmering cocktail evening dress, stiletto heels, golden belt.
  4. *Tier 4 (Royal Princess)*: Flowing emerald ballgown, princess tiara, radiant sparkles.
  5. *Tier 5 (Imperial Majestic Queen 👑)*: Grand embroidered golden gown, flowing royal velvet cape/train, and the massive Imperial Diamond Crown!
- 👑 **Coronation Finale Transformation**: End-of-run multiplier staircase (1.0x to 5.0x), majestic golden throne dais, coronation pirouette, crown descent, and dual confetti cannon blasts!
- 🏆 **5 Progressive Levels**:
  - **Level 1**: *The Debutante Walk* (Palace Gardens) - Gentle speed, foundational gates.
  - **Level 2**: *Fashion Promenade* (Gilded Boulevard) - Faster speed, mud puddles introduced.
  - **Level 3**: *The Royal Gala* (Imperial Plaza) - Moving oscillating gates, S-curve coins.
  - **Level 4**: *Chamber of Mirrors* (Rose Gold Palace) - Rapid choices, high stakes.
  - **Level 5**: *The Grand Coronation* (Imperial Citadel) - Ultimate royal gauntlet, maximum multipliers!
- 📱 **Mobile Touch Controls**: Responsive 1:1 finger drag or horizontal swipe anywhere on screen.
- ⌨️ **Desktop Keyboard Controls**: `A` / `D` or `Left` / `Right` Arrow keys, plus mouse drag.
- 🔊 **Procedural Web Audio Engine**: Zero external MP3/WAV assets needed! Includes background electronic catwalk music groove, coin chimes, gem arpeggios, positive/negative gate chords, level-up fanfares, and imperial coronation trumpet brass.
- 🎥 **Third-Person Chase Camera**: Dynamic framing that smoothly tracks the queen with cinematic finish shots.
- ✨ **Glassmorphism Mobile HUD**: Real-time glamour progress bar, tier badges, coin counters, level badges, and animated floating 3D text popups (`+35 GLAMOUR!`).

---

## 🚀 Quick Start Guide

### Option 1: Direct Browser Launch (Simplest)
Double-click `start.bat` or open `index.html` directly in any web browser (Google Chrome, Microsoft Edge, Safari, Firefox).
Because all 3D assets, textures, and sounds are generated procedurally, the game runs **100% offline** without needing a web server or CORS configurations!

### Option 2: Local HTTP Server (PowerShell)
Run the included PowerShell server script:
```powershell
powershell -ExecutionPolicy Bypass -File .\serve.ps1
```
This starts a built-in .NET HTTP server at `http://localhost:8080` and opens your browser automatically.

---

## 🎮 How to Play & Controls

| Input Device | Action |
| :--- | :--- |
| **Mobile / Tablet** | Touch anywhere and drag your finger left/right to steer the Queen across lanes. |
| **Desktop Keyboard** | Press `A` or `Left Arrow` to steer left; press `D` or `Right Arrow` to steer right. |
| **Desktop Mouse** | Click and drag horizontally across the screen. |
| **Audio Toggle** | Click the 🔊 button in the top right corner to mute/unmute SFX and music. |

### Objectives:
1. Walk through **Green / Gold** positive fashion gates to increase your Glamour.
2. Avoid **Red / Dark** negative gates and mud puddles to avoid losing Glamour.
3. Collect golden coins and royal gems along the way.
4. Reach the finish line with maximum Glamour to climb higher on the multiplier staircase and sit on the **Imperial Golden Throne**!

---

## 📁 Project Architecture

```
queen-runner/
│
├── index.html            # Main HTML5 entry point & UI overlay container
├── README.md             # Documentation, expansion guides, and feature breakdown
├── serve.ps1             # Lightweight PowerShell web server (.NET HttpListener)
├── start.bat             # Windows one-click launcher
│
├── css/
│   └── style.css         # Glassmorphism styling, responsive HUD, modal animations
│
└── js/
    ├── audio.js          # Procedural Web Audio synthesizer (SFX & Catwalk BGM)
    ├── character.js      # Procedural 3D Queen rig, skeletal animation, 5 outfit tiers
    ├── environment.js    # Royal runway, towers, cherry trees, paparazzi flashes, throne
    ├── gates.js          # 3D choice gates with dynamic text textures & collisions
    ├── collectibles.js   # 3D spinning coins, gems, mud hazards, magnetism suction
    ├── levels.js         # Level 1-5 definitions, speeds, gate pairs, coin layouts
    └── game.js           # Core Babylon.js loop, camera chase, input, UI state machines
```

---

## 🛠️ Instructions for Expanding the Game

### 1. Adding New Levels
To add a Level 6 or modify existing tracks, open `js/levels.js` and add a new object to the `GAME_LEVELS` array:

```javascript
{
    id: 6,
    title: "The Celestial Gala",
    subtitle: "Sky Palace",
    length: 500,
    speed: 21.0,
    targetGlamour: 150,
    description: "An ethereal runway among the clouds!",
    gates: [
        {
            z: 40,
            left: { text: "STAR DUST", delta: 50, isPositive: true },
            right: { text: "SHADOWS", delta: -40, isPositive: false }
        },
        {
            z: 85,
            isMoving: true,
            moveSpeed: 4.2,
            moveAmp: 1.2,
            left: { text: "SUN DIADEM", delta: 60, isPositive: true },
            right: { text: "COLD RAIN", delta: -45, isPositive: false }
        }
    ],
    coins: [
        { type: "arc", startX: -1.6, endX: 1.6, startZ: 15, count: 8 },
        { type: "line", x: 0, startZ: 50, count: 6 }
    ],
    gems: [
        { x: 0, z: 25, type: "ruby" }
    ],
    hazards: [
        { x: -1.6, z: 65 }
    ]
}
```

### 2. Creating New Outfit Tiers & Accessories
Open `js/character.js`:
- To add a new material or color palette, update `initMaterials()` with `createMat(...)`.
- To attach custom meshes (e.g., wings, floating pets, handbags), instantiate a Babylon mesh in `buildRig()` and parent it to `this.parts.chest`, `this.parts.pelvis`, or `this.parts.armR.hand`.
- To add an outfit tier (e.g., Tier 6 - Celestial Empress), update `applyTier(tier)` and the tier check in `js/game.js` (`syncCharacterOutfit`).

### 3. Loading External 3D Models (.GLTF / .GLB)
If you wish to replace procedural character meshes with Blender/Mixamo models:
1. Include the Babylon loaders script in `index.html`:
   ```html
   <script src="https://cdn.babylonjs.com/loaders/babylonjs.loaders.min.js"></script>
   ```
2. In `character.js`, replace the procedural rig with:
   ```javascript
   BABYLON.SceneLoader.ImportMesh("", "./assets/", "queen_model.glb", this.scene, (meshes, particleSystems, skeletons, animationGroups) => {
       const model = meshes[0];
       model.parent = this.root;
       // Play imported run animation
       animationGroups[0].play(true);
   });
   ```

### 4. Adding New Collectibles & Powerups
Open `js/collectibles.js`:
- Add a new method such as `spawnMagnetPowerup(x, z)` or `spawnSpeedBoost(x, z)`.
- When collected in `js/game.js` (`onCollectItem`), apply temporary effects such as doubling coin attraction radius or granting an invulnerability shield against mud!

### 5. Customizing Sound & Music
Open `js/audio.js`:
- Change the background music BPM by modifying `this.tempo = 124`.
- Change musical notes in `scheduleBeat()` or modify synthesizer waveforms (`'sine'`, `'triangle'`, `'sawtooth'`).
