# xmas ref from bvd0101



\# Magic Christmas Project
python3 -m http.server 8000

http://localhost:8000 

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



