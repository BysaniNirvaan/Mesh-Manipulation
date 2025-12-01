🧵 Interactive Cuttable Cloth (Three.js)

A fully interactive cloth/jeans cutting simulation built using Three.js, featuring real-time physics, verlet integration, dynamic spring constraints, and triangle-removal based mesh cutting.

This project lets you click + drag to cut the cloth, and the cut pieces will fall down naturally with gravity and physics.

📄 Reference Source: index.html

⭐ Features

✔️ Realistic cloth physics using Verlet integration

✔️ Smooth cutting using:

Triangle removal

Spring deactivation

Cut-path intersection detection

✔️ Cloth tears apart naturally & falls down

✔️ Pinned top row (like a flag or jeans piece hanging)

✔️ Dynamic mesh rebuilding after cuts

✔️ High resolution mesh for smooth cuts

✔️ OrbitControls camera

✔️ Shadows, lights, and ground collision

🎥 Demo Controls
Action	Description
Click + Drag	Cut the cloth along the drag path
Scroll	Zoom in/out
Right mouse drag	Move camera
Left mouse drag (outside cloth)	Rotate scene
📦 Installation & Run
1. Clone the repository
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name

2. Open the project

No build tools needed — completely client-side.

Just open index.html in a browser:

# For VS Code users:
Live Server → Open index.html

# OR simple Python server:
python3 -m http.server


Then run:

http://localhost:8000

🧠 How It Works
🔹 Cloth Structure

The cloth is created from a PlaneGeometry divided into a grid:

const clothGeometry = new THREE.PlaneGeometry(clothSize, clothSize, gridSize, gridSize);


Each vertex becomes a particle with physics.
Edges between vertices become springs (constraints).

🔹 Physics Engine

A custom cloth engine using:

Verlet Integration

Gravity

Spring constraints

Damping

Multiple constraint passes for stability

Particles on the top row are pinned:

const invMass = isTopRow ? 0 : 1;

🔹 Cutting System

When the user drags:

Raycaster detects the cut point

Nearby triangles (within radius) are removed

Springs are disabled

Mesh index buffer is rebuilt

Cloth splits naturally and falls

This ensures clean natural tearing instead of glitchy holes.

📁 Project Structure
├── index.html   <-- main file (Three.js cutting cloth simulation)
└── README.md    <-- this file

⚙️ Customization

You can tweak physics inside:

const SETTINGS = {
    gridSize: 40,
    clothSize: 10,
    stiffness: 0.8,
    damping: 0.98,
    gravity: -9.8,
    cutRadius: 0.8,
};

🧪 Browser Compatibility

Works on:

Chrome ✔️

Edge ✔️

Firefox ✔️

Safari (WebGL enabled) ✔️

🙌 Credits

Built with Three.js

Physics engine & cutting logic fully custom
