# VR Dream Villa – A‑Frame Experience
An immersive 3D villa environment built with [A‑Frame](https://aframe.io/). Explore three furnished rooms (living room, bedroom, kitchen), an animated swimming pool, a garden with trees and a pet dog, and more. The scene is designed for VR headsets and desktop browsers with mouse/keyboard controls.

## Features
- **Three fully furnished rooms** with furniture, lighting, and decorations.
- **Animated swimming pool** – water ripples using a custom sine‑wave script.
- **Interactive controls** – WASD movement + mouse drag (or VR headset).
- **Outdoor elements** – trees, a car, a dog, outdoor string lights, and a bench.
- **Dynamic animations** – rotating ceiling fan, bobbing pool duck, and a wiggling dog.
- **Imported 3D model support** – the villa itself is a high‑quality GLB model (`the_dream_house.glb`).

## Project Structure
EXAMINATION/
├── assets/
│ └── models/
│ ├── the_dream_house.glb
├── index.html

## Requirements
- A modern web browser (Chrome, Firefox, Edge) with WebGL support.
- A local web server (due to browser security restrictions on loading local models).  
  See [How to Run](#how-to-run) below.

## How to Run
### Option 1: VS Code Live Server (recommended)
1. Open the project folder in Visual Studio Code.
2. Right‑click `index.html` and select **Open with Live Server**.
3. The page will open automatically at `http://127.0.0.1:5500`.

### Option 2: Python 3 HTTP Server
1. Open a terminal/command prompt inside the project folder.
2. Run:  
   `python -m http.server 8000`
3. Open your browser and go to `http://localhost:8000`.

### Option 3: Node.js live-server
1. Install `live-server` globally: `npm install -g live-server`
2. In the project folder, run: `live-server`

## Controls
| Action            | Desktop                         | VR Headset                      |
|-------------------|---------------------------------|---------------------------------|
| Look around       | Mouse drag / click + drag       | Head tracking                   |
| Move              | W, A, S, D keys                 | Controller thumbstick (if supported) |
| Teleport          | Not implemented                 | Use the cursor (click/tap)      |

The camera starts at a comfortable distance from the villa.

## Customization
### Switching to a Different 3D Model
The current model is `the_dream_house.glb`. To use another model:
1. Change the `<a-asset-item>` `src` attribute inside `<a-assets>`:
   ```html
   <a-asset-item id="dreamHouse" src="assets/models/modern_house.glb"></a-asset-item>
   
2. The model will load automatically when you refresh the page.

Adjusting Model Position, Scale, or Rotation
Find the <a-entity> that loads the model and modify its attributes:

html
<a-entity gltf-model="#dreamHouse" position="0 0 0" scale="1 1 1" rotation="0 0 0"></a-entity>
position="x y z" – moves the model (try 0 -0.2 0 to lower it).

scale="sx sy sz" – resizes the model (smaller values like 0.5 shrink it).

rotation="x y z" – rotates the model (use 0 90 0 to face a different direction).

Removing the Pool Animation
The water ripple is controlled by a script at the end of the file. To disable it, delete or comment out this line:

javascript
document.querySelector('#waterPlane').setAttribute('water-ripple', '');
Adding or Removing Objects
The scene is built entirely with A‑Frame entities. You can add, remove, or edit any element by modifying the HTML.

Technical Notes
The water animation uses a custom A‑Frame component (water-ripple) that updates the water plane’s Y‑position with a sine wave, creating a gentle ripple effect without a heavy physics engine.

Shadows are enabled for the directional light and key objects to improve realism.

The scene is optimized for performance: shadows are limited to 1024×1024 resolution, and most geometry uses low‑poly primitives.
