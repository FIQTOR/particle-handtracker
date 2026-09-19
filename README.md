
# 🌌 Gesture Controlled 3D Particles

An interactive 3D WebGL experience using **Three.js** and **MediaPipe Hand Landmarker**. This web application renders 25,000 GPU-accelerated particles that reform into various 3D parametric shapes and react in real-time to hand gestures detected via your webcam.

---

## ✨ Features

- 🖐️ **Real-time AI Gesture Tracking**: Expands (explodes) and contracts (forms shapes) particles based on hand openness using MediaPipe Vision Tasks API.
- 🎨 **Dynamic 3D Shapes**: Smooth CPU/GPU transitions between multiple 3D models:
  - 💖 Heart (Parametric 3D volume)
  - 🪐 Saturn (Planet body with tilted rings)
  - 🌸 Flower (Rose curve formula)
  - 🧘 Statue / Buddha (Meditating silhouette)
  - 🎆 Bang / Fireworks (Wispy explosion trails)
  - 🔮 Sphere (Uniform spherical distribution)
- ⚡ **Custom GLSL Shaders**: Uses custom Vertex and Fragment shaders featuring Simplex noise, additive blending, and point-size attenuation for realistic glowing particle effects.
- 🎛️ **Interactive Controls**:
  - Live webcam feedback feed overlay.
  - Custom color picker to change particle hues dynamically.
  - Manual expansion slider fallback when a camera is unavailable or disabled.
- 💎 **Modern UI/UX**: Sleek dark glassmorphism interface built with Tailwind CSS.

---

## 🛠️ Tech Stack & Dependencies

- **HTML5 & CSS3**
- **[Three.js (r128)](https://threejs.org/)** — WebGL 3D graphics rendering engine.
- **[MediaPipe Tasks Vision](https://developers.google.com/mediapipe/tasks/vision/hand_landmarker)** — Machine learning hand tracking and landmark extraction.
- **[Tailwind CSS](https://tailwindcss.com/)** — Utility-first CSS styling.
- **GLSL** — Shader programming for custom particle noise and displacement effects.

---

## 🚀 Getting Started

Since this project uses client-side WebGL and ESM modules loaded via CDNs, no installation or build process (like `npm install`) is strictly required to run it locally.

### Prerequisites
- A modern web browser with **WebGL** support (Chrome, Edge, Firefox, Safari).
- A working webcam (for hand tracking features).

### Quick Start
1. Clone this repository:
   ```bash
   git clone [https://github.com/your-username/gesture-controlled-3d-particles.git](https://github.com/your-username/gesture-controlled-3d-particles.git)
   cd gesture-controlled-3d-particles

```

2. Serve the directory using a local web server (required for MediaPipe WASM and webcam permissions):
* **Using VS Code**: Install the [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer&utm_source=gemini) extension, right-click `index.html`, and select **"Open with Live Server"**.
* **Using Python**:
```bash
python3 -m http.server 8000

```


Then open `http://localhost:8000` in your browser.
* **Using Node.js (`npx`)**:
```bash
npx serve .

```




3. Allow camera access when prompted by the browser.

---

## 🎮 How to Control

### 🖐️ Hand Gestures

* **Open Hand / Spread Fingers**: Expands particles outward into a chaotic, diffused cloud.
* **Closed Fist**: Contracts particles back into the selected 3D shape.

### 🎛️ On-Screen Panel

* **Model Shape**: Click any shape button (*Heart, Saturn, Flower, Statue, Bang, Sphere*) to transition the target shape.
* **Particle Color**: Use the color picker to set custom particle glow colors.
* **Expansion Slider**: If no hand is detected or if camera access is turned off, manually control particle explosion using the slider.

---

## ⚙️ How It Works

1. **Vision Engine**: MediaPipe processes webcam frames at runtime, calculating the distance between the **Wrist Landmark (`0`)** and **Middle Finger Tip (`12`)** relative to palm width to compute a normalized `openness` index (`0.0` to `1.0`).
2. **Buffer Geometry Interpolation**: Position updates smoothly transition `target` vertex attributes when switching models.
3. **GLSL Shader Processing**: The vertex shader mixes the baseline shape position with custom Simplex noise displacement (`aRandom`) driven by the `uExpansion` uniform value.

---

## 📜 License

Distributed under the MIT License. Feel free to fork, modify, and build upon this project!

```
