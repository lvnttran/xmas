# xmas



\# Magic Christmas Project



\## Overview

This is a single-file HTML/JS web application that uses Three.js for 3D rendering and MediaPipe Hands for gesture control. It creates an interactive Christmas scene with particle effects (Tree, Heart, Explosion, Snow, Earth) controlled by hand gestures.



\## Development



\### Prerequisites

\- A modern web browser with WebGL and Camera support.

\- Internet connection (to load CDN scripts for Three.js and MediaPipe).



\### Running the Project

Since this project uses ES modules and camera access, it is best run via a local web server to avoid CORS issues with local file access (though the current script tags are global, camera permissions often require HTTPS or localhost).



\*\*Using Python:\*\*

```bash

python3 -m http.server 8000

\# Open http://localhost:8000 in your browser

```



\*\*Using Node.js (npx):\*\*

```bash

npx serve .

\# Open the provided URL in your browser

```



\## Architecture



\### Core Components

\- \*\*index.html\*\*: Contains all HTML, CSS, and JavaScript.

\- \*\*Three.js\*\*: Handles the 3D scene, camera, renderer, and particle systems.

\- \*\*MediaPipe Hands\*\*: Handles hand tracking and gesture recognition.



\### Key Functions

\- `init3D()`: Initializes the Three.js scene, camera, renderer, and particle groups.

\- `createParticleSystem(type, count, size)`: Creates particle systems (Gold, Red, Gift) with pre-calculated target positions for different states (Tree, Heart, Explode, Earth).

\- `createSnowSystem(count)`: Creates the falling snow particle system.

\- `createSanta()`: Creates the flying Santa sprite and his magic trail particle system.

\- `createEarthFlags()`: Creates cute, rounded sprites for Vietnam and France flags on the Earth globe.

\- `initGiftPool()`: Initializes a pool of gift sprites for the burst effect.

\- `spawnGiftBurst(pos)`: Triggers a burst of gifts at the specified position.

\- `updateParticleGroup(...)`: Interpolates particle positions between current and target states, and handles state-specific animations (rotation, twinkling, pulsing).

\- `updateSnow()`: Updates snow particle positions (falling and resetting).

\- `updateSanta(time)`: Animates Santa flying across the screen and updates the trail particles.

\- `updateGifts()`: Updates the physics of active gift burst particles.

\- `startSystem()`: Initializes the camera and MediaPipe Hands detector.

\- `animate()`: The main render loop.



\### States

The application switches between states based on hand gestures:

\- \*\*TREE\*\*: Default state. Particles form a layered Christmas tree shape.

\- \*\*HEART\*\*: Triggered by "Heart" gesture (two hands forming a heart). Particles form a 3D heart.

\- \*\*EXPLODE\*\*: Triggered by "Open Hand". Particles explode outward.

\- \*\*PHOTO\*\*: Triggered by "Pinch" (thumb and index close). Shows photo gallery with captions.

\- \*\*EARTH\*\*: Triggered by catching Santa. Particles form a rotating Earth globe with Vietnam and France highlighted, connected by a golden arc, and displaying cute national flags.



\### Interactions

\- \*\*Catch Santa\*\*: Pointing at the flying Santa with your index finger triggers a burst of gifts and switches the scene to the Earth animation.

\- \*\*Exit Earth\*\*: To exit the Earth animation, perform an "Open Hand" (Explode) gesture.



\## Assets

\- Images are loaded from relative paths (`./image1.jpeg`, etc.).

\- Audio is loaded from `./audio.mp3`.

\- Textures are procedurally generated via `createCustomTexture()` or loaded from images.

\- Captions are defined in the `photoCaptions` array in `index.html`.



