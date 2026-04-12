# Premium Gallery Laptop Boutique

A 3D interactive showroom built with Three.js. Features a gallery lounge with glass shelves, realistic laptop displays, and a staff store room.

## Deploy to Vercel (Free)

### Option A — Vercel CLI (fastest)
```bash
npm i -g vercel
vercel
```
Follow the prompts. Done. Your site is live.

### Option B — GitHub + Vercel Dashboard
1. Create a new GitHub repo (public or private)
2. Push these two files:
   - `index.html`
   - `vercel.json`
3. Go to [vercel.com](https://vercel.com) → **Add New Project**
4. Import your GitHub repo
5. Framework Preset: **Other**
6. Click **Deploy**

Vercel auto-deploys on every push to `main`.

## Controls
- **Drag** — Look around
- **Scroll** — Zoom in / out
- **Buttons** — Switch between Gallery Lounge and Staff Store Room

## What Changed vs Original
- Fixed loading-stuck bug: switched from `<script src>` CDN tag to **ES Module importmap** (Three.js r158). The old r128 CDN script had a race condition where the scene tried to initialize before `THREE` was globally defined in some Vercel/browser environments.
- Overlay now hides only after the first render frame completes — guaranteed no stuck loading screen.
- Materials upgraded:
  - **Glass** uses `MeshPhysicalMaterial` with `transmission`, `ior`, `clearcoat`, `thickness` — actual refraction, not fake opacity
  - **Laptops** have brushed metal texture maps, proper `envMap` reflections, realistic roughness/metalness
  - **Screens** show a code editor mockup texture with a subtle screen glow point light
  - **Floor** has marble vein texture + normal map for surface depth
  - **Walls** have subtle stucco noise texture
  - **Gold** fixtures have high-intensity env reflections
- Environment map is procedurally generated (no external HDR file needed — works offline and on free hosting)
- Laptop model upgraded: separate bezel, trackpad, keyboard area, hinge group, and per-screen glow light

