# 🦁 Zoo Builder: 3D Reaction Timer

**A gamified reaction time test measuring cognitive processing speed using procedural 3D graphics.**

![Project Status](https://img.shields.io/badge/status-live-success) ![Tech](https://img.shields.io/badge/tech-Three.js%20|%20Vanilla%20JS-blue)

## 📋 Overview

**Zoo Builder** is a portfolio project designed to demonstrate advanced frontend development skills, 3D graphics integration, and UX precision. Unlike standard reaction timers that simply change background colors, this application utilizes **Three.js** to render a rapid-cycling carousel of 3D animals.

The user must react immediately when the cycling stops and a distinct animal appears. Successful reactions add the animal to the user's "Zoo Collection," gamifying the experience and encouraging repeated trials.

## ✨ Key Features

*   **Interactive 3D Graphics:** Real-time rendering of procedurally generated block-style animals (Lion, Elephant, Zebra, Giraffe, Hippo) using Three.js.
*   **Precision Timing:** Utilizes `performance.now()` for high-resolution millisecond accuracy (sub-millisecond precision floating point).
*   **Edge Case Handling:** Includes robust false-start detection for pre-emptive clicking functionality.
*   **Responsive Design:** Fully fluid layout that adapts the 3D viewport and UI for mobile, tablet, and desktop devices.
*   **Session Statistics:** Tracks current session attempts, calculating real-time averages and highlighting personal bests.
*   **Zero-dependency architecture:** Built as a single HTML artifact with no local build steps required.

## 🛠️ Technical Stack

*   **Core:** HTML5, CSS3, Vanilla JavaScript (ES6+ classes).
*   **3D Engine:** [Three.js](https://threejs.org/) (via CDN).
*   **Typography:** Google Fonts (Inter for UI, Poppins for headings).
*   **Architecture:** Object-Oriented Programming (OOP) with separate classes for `GameEngine` (logic) and `SceneManager` (visuals).

## 🚀 Quick Start

Because this project is built as a portable single-file artifact, no build process (Webpack/Vite) is active.

1.  **Download** the `index.html` file.
2.  **Open** the file in any modern web browser (Chrome, Firefox, Safari, Edge).
3.  **Play:** Click "Start Game" to begin the simulation.

## 🧠 Engineering Highlights

### 1. Procedural 3D Generation
To keep the application lightweight and performant, external `.obj` or `.gltf` models are avoided. Instead, `SceneManager` procedurally generates animals using `THREE.Group` and primitive geometries (`BoxGeometry`).
*   *Benefit:* zero asset loading time, immediate startup, and demonstrates understanding of 3D coordinate systems and scene graphs.

### 2. State Machine Logic
The game relies on a strict internal state machine to manage UI and user inputs, preventing race conditions or logic errors.
*   `IDLE`: Main menu, steady rotation.
*   `CYCLING`: Rapidly swapping meshes, input waits (or triggers penalty).
*   `WAITING_FOR_INPUT`: Timer running, looking for `mouseup`.
*   `FINISHED`: Result display and cleanup.

### 3. Performance Optimization
*   **Rendering:** The animation loop uses `requestAnimationFrame` for smooth 60fps rendering.
*   **Garbage Collection:** Geometries and materials are managed carefully; the scene explicitly removes old meshes before adding new ones to prevent memory leaks during rapid cycling.

## 🎨 Design System

The UI uses a modern "Dark Mode" aesthetic suited for technical dashboards:

*   **Background:** Slate Dark (`#0F172A`)
*   **Surface:** Slate Light (`#1E293B`)
*   **Accents:**
    *   Ready/Success: Emerald (`#10B981`)
    *   Waiting: Amber (`#F59E0B`)
    *   Action: Blue (`#3B82F6`)
    *   Error: Red (`#EF4444`)

## 🔮 Future Improvements

While this version is optimized for portability:

*   **Persistence:** Integrate `localStorage` to save high scores across browser sessions.
*   **Audio:** Add spatial audio cues using `THREE.AudioListener` for state changes.
*   **Physics:** Implement `Cannon.js` for more dynamic animal entry animations (dropping/bouncing).

## 📄 License

MIT License. Free to use for educational purposes and portfolio demonstrations.

---
*Created by Leon James*
