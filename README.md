<div align="center">

# ◉ Black Hole Simulation

[English](README.md) · [Türkçe](README.tr.md)

**Real-time general relativistic ray tracing in your browser.**

Explore how light bends around a rotating black hole: move the camera, adjust physical parameters, and fall toward the event horizon.

`WebGL 2` · `Vanilla JavaScript` · `GLSL` · `No dependencies`

</div>

---

## Features

| Visualization | Interaction |
| :--- | :--- |
| Per-pixel geodesic ray tracing through curved spacetime | Cinematic, free camera, auto orbit, and free fall modes |
| Gravitational lensing, black hole shadow, and photon ring | Spin, inclination, distance, field of view, and disk controls |
| Novikov–Thorne thin disk, Doppler effect, and gravitational redshift | Eight presets, quality settings, and screenshots |
| Procedural stars, Milky Way, and optional relativistic jet | Light path diagram and simulated EHT view |

## Run locally

Use a modern browser with **WebGL 2** support. No installation or package manager is required.

```bash
python -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000). You can also open `index.html` directly in your browser.

> Visual quality and frame rate depend on your GPU. Lower the ray tracing quality in the right-hand panel if needed.

## Controls

| Action | Control |
| :--- | :--- |
| Rotate / look around | Drag / `Shift` + drag |
| Zoom in or out | Mouse wheel |
| Cinematic / free / fall mode | `C` / `O` / `D` |
| Select a preset | `1`–`8` |
| Toggle auto orbit / pause time | `T` / `Space` |
| Toggle UI / settings / information | `H` / `P` / `I` |
| Full screen / screenshot | `F` / `S` |

## How it works

Light rays are traced using Hamilton's equations. The CPU physics core is in `js/physics.js`; the GLSL ray tracer and rendering passes are in `js/shaders.js`. `js/main.js` handles the camera, WebGL pipeline, and interface. Disk temperature follows the Novikov–Thorne model, while stars and disk textures are generated in code without external image files.

The EHT view is a **visual approximation** of telescope resolution; it does not use real telescope data.

## Validation

The physics core is checked against analytical results for the shadow, critical orbits, ISCO, and free fall:

```bash
node dev/test_physics.js
```

## Project structure

```text
index.html           Interface and entry point
js/physics.js        Black hole physics and geodesic calculations
js/shaders.js        GLSL ray tracing and rendering
js/main.js           Camera, WebGL pipeline, and interaction
dev/                 Physics tests and development tools
```
