# Product Studio

A browser-based 3D product visualizer built with [Three.js](https://threejs.org/). Load any `.glb` model and compose it with real-time lighting, backdrop colors, and camera presets — then export a PNG snapshot.

![Product Studio](https://img.shields.io/badge/Three.js-r160-black?logo=threedotjs) ![License](https://img.shields.io/badge/license-MIT-blue)

---

## Features

- **3-point lighting rig** — Key, Fill, and Rim lights with independent intensity, angle, and color controls
- **8 lighting presets** — Natural, Drama, Sunset, Clean, Neon, Overcast, Spotlight, Warm Studio
- **Backdrop color** — 12 curated swatches + custom color picker; seamlessly tints the infinity-cove cyclorama
- **Camera presets** — Front, Side, Top, ¾ Low, Hero, Macro with smooth animated transitions
- **OrbitControls** — drag to orbit, scroll to zoom
- **Options** — auto-rotate, shadow, and ground plane toggles
- **Snapshot export** — saves the canvas as a timestamped PNG

## Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/your-username/product-studio.git
cd product-studio
```

### 2. Add your model

Place your `.glb` file in the project root and update the loader path in `index.html`:

```js
// index.html — find this line and replace 'band.glb' with your filename
new GLTFLoader().load('your-model.glb', gltf => {
```

> **Mesh naming:** The loader assigns a matte-plastic material to any mesh named `Object_1`. All other meshes receive a metallic material. Adjust the `traverse` block in `index.html` to match your model's mesh names.

### 3. Serve locally

Because the page uses ES modules and loads a `.glb` file, it must be served over HTTP — opening `index.html` directly as a `file://` URL will not work.

**Option A — Python (no install needed):**
```bash
python3 -m http.server 8080
# open http://localhost:8080
```

**Option B — Node / npx:**
```bash
npx serve .
```

**Option C — VS Code:**  
Install the [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension and click **Go Live**.

---

## Project Structure

```
product-studio/
├── index.html      # Full application — HTML, CSS, and JS in one file
├── band.glb        # (example model — replace with your own)
└── README.md
```

All Three.js dependencies are loaded from a CDN (`jsdelivr.net`) — no build step or `npm install` required.

## Deployment

The app is a single static file and deploys to any static host:

- **GitHub Pages** — push to `main`, enable Pages under *Settings → Pages*, set source to the repo root.
- **Netlify / Vercel** — drop the folder or connect the repo; no build command needed.
- **Any web server** — copy `index.html` and your `.glb` to the same directory.

## Controls Reference

| Input | Action |
|---|---|
| Left-drag | Orbit |
| Right-drag / two-finger drag | Pan |
| Scroll / pinch | Zoom |
| Panel sliders | Adjust lights live |
| Swatch / color picker | Change backdrop |
| Camera buttons | Animated camera jump |
| ⬡ Capture Snapshot | Save PNG |

## Dependencies

| Library | Version | Source |
|---|---|---|
| Three.js | r160 | jsdelivr CDN |
| GLTFLoader | r160 | jsdelivr CDN |
| OrbitControls | r160 | jsdelivr CDN |
| RGBELoader | r160 | jsdelivr CDN |
| DM Mono | — | Google Fonts |
| Instrument Serif | — | Google Fonts |

No bundler. No framework. No `node_modules`.

## License

MIT — use it, fork it, ship it.
