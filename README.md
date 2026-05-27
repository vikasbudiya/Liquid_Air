# Liquid Surface

An experimental, interactive WebGL art project that simulates a living transparent liquid surface floating in front of your camera. It responds to hand gestures in real time using camera-based computer vision, generating optical refraction, physical wakes, floating debris, and responsive ASMR-style water acoustics.

## Core Features

- **Interactive Fluid Simulation**: Real-time shallow water equation solver rendered in WebGL, supporting up to 24 simultaneous ripple sources.
- **Dynamic Camera Refraction**: Live front/back camera streams refracted through the simulated fluid surface, using high-end glass aesthetics, chromatic aberration, caustics, and iridescence.
- **WebGL-Refracted 2D Elements**: Floating dry leaves and speed-reactive bubbles simulated in 2D canvas but uploaded as a dynamic GPU texture, allowing them to bend and distort with the water ripples.
- **Adaptive One-Euro Filtering**: Multi-axis tracking filters that adapt dynamically to frame rate (60Hz to 120Hz), removing tracking jitter while maintaining responsiveness.
- **Responsive ASMR Audio Engine**: Synthesized water acoustics (ambient hums, sloshing, splashes, drips, and bubble pops) mapped non-linearly to hand velocity.
- **Integrated Control Panel**: Adjust sensitivity, ripple intensity, viscosity, glow, color tint, and active simulation modes in real time.
- **On-Screen Recording & Capture**: Capture high-quality PNG screenshots or record `.webm` video clips of your interaction directly from the WebGL buffer.

## Tech Stack

- **Graphics**: WebGL via [Three.js](https://threejs.org/) (r160)
- **Computer Vision**: [MediaPipe Tasks Vision](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker) (Hand Landmarker)
- **Acoustics**: Web Audio API (real-time brown noise synthesis & sweeping filters)
- **Structure**: Single-file static HTML5 & ES modules

## Quick Start

The experience requires camera access to detect hands and render the live background membrane. 

Since WebGL and MediaPipe models load via CDN and require security headers, the page must be served through a local server:

1. Navigate to the project folder:
   ```bash
   cd Liquid-surface
   ```

2. Start a local HTTP server (e.g., using Python 3):
   ```bash
   python3 -m http.server 8080
   ```

3. Open your browser and visit:
   ```
   http://localhost:8080
   ```

4. Grant camera permission when prompted, and press **Enter** to start the experience.

## Interaction Guide

- **Camera Control**: Hover your hand in front of the camera. The vision model tracks your fingertips and palm center, creating dynamic ripples and ripples wakes behind floating leaves.
- **Mouse / Touch Fallback**: If a camera is unavailable or tracking is turned off, drag on the canvas to interact.
- **Control Panel**: Use the menu in the top-right corner to change water presets (Gentle Water, Elastic, Viscous, Neon Plasma), tweak physics values, or change the color tint.
- **Keyboard Shortcuts**: Double-click anywhere on the screen (outside the controls panel) to toggle a real-time FPS counter.
