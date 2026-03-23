# 🌌 Black Hole Simulation

A real-time WebGL black hole simulation running entirely in the browser — no libraries, no frameworks, just raw GLSL shaders.

![Black Hole Simulation](demo.gif)

---

## ✨ Features

- **Gravitational Lensing** — Light rays bend around the black hole using a Schwarzschild metric approximation
- **Accretion Disk** — Animated, glowing disk with realistic ring structure
- **Doppler Effect** — Blueshift on the approaching side, redshift on the receding side
- **Star Field** — Dynamic background with density clustering near the black hole
- **Adaptive Ray Marching** — Step size adjusts based on proximity to the singularity

---

## 🚀 Live Demo

Just open `index.html` in any modern browser — no build step, no dependencies.

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
open index.html   # macOS
# or just double-click index.html on Windows/Linux
```

---

## 🛠️ How It Works

The simulation uses a **fragment shader** running on the GPU. For every pixel on screen:

1. A ray is cast from the camera into the scene
2. At each step, a gravity force pulls the ray toward the black hole center (approximating geodesic paths in curved spacetime)
3. If the ray crosses the **Schwarzschild radius** → black hole (no light escapes)
4. If the ray passes through the **accretion disk plane** → disk color is accumulated with Doppler shift
5. If the ray escapes → the star field background is sampled

```
Camera → Ray Marching Loop → [Event Horizon | Accretion Disk | Background]
```

---

## ⚙️ Tweakable Parameters

Inside `index.html`, in the fragment shader:

| Parameter | Default | Description |
|-----------|---------|-------------|
| `bhMass` | `1.2` | Black hole mass (affects Schwarzschild radius) |
| `outerRadius` | `0.978` | Star density zone around the black hole |
| `powerExp` | `300–50` | Star density (lower = denser) |
| `distXZ` range | `Rs*1.5 – 14.0` | Accretion disk inner/outer radius |
| `iTime * 2.0` | — | Disk rotation speed |

---

## 📸 Capturing the GIF

To create `demo.gif` for this README:

1. Open `index.html` in Chrome
2. Use **[ScreenToGif](https://www.screentogif.com/)** (Windows) or **[Kap](https://getkap.co/)** (macOS)
3. Record 3–5 seconds of the simulation
4. Export as `demo.gif` and place it in the repo root
5. The README will pick it up automatically ✅

---

## 📄 License

MIT — do whatever you want with it.
