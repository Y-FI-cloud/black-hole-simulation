# 🌌 Black Hole Simulation

A real-time WebGL black hole simulation running entirely in the browser — no libraries, no frameworks, just raw GLSL shaders.


![B-H-S](https://github.com/user-attachments/assets/2d6d61f6-e08e-4fc7-9807-2a513ac9b0e3)

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
Link :  https://y-fi-cloud.github.io/black-hole-simulation/
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
