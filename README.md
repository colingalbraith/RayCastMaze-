
# RayCastMaze

## Introduction

A 3D procedurally generated maze game built using Python and basic libraries like `numpy` and `matplotlib`. The game draws inspiration from old-school forced perspective games, using 2D ray casting to simulate 3D visuals. The player navigates through a procedurally generated maze, using simple keyboard inputs to move forward, backward, and rotate. The maze and walls are dynamically generated at runtime, providing a unique experience every time the game is played.

Below, you can see the progression of the project from start to the final product, including videos of me stumbling through one of the procedural mazes.

### Project Demos:

![Progress 1](https://github.com/colingalbraith/RayCastMaze-/assets/146497900/8df17009-0b11-4788-91a7-bc77d2d8dcb9)
![Progress 2](https://github.com/colingalbraith/RayCastMaze-/assets/146497900/71bf772f-3e76-478f-bd9c-8eee26087ab0)

https://github.com/colingalbraith/RayCastMaze-/assets/146497900/25519102-8699-4216-9015-a76224dd48e3


https://github.com/colingalbraith/RayCastMaze-/assets/146497900/0a82f2ed-af5a-4818-986d-adb658640e28


https://github.com/colingalbraith/RayCastMaze-/assets/146497900/c3f7837e-fc00-4d65-b85f-d7f97432a836



https://github.com/colingalbraith/RayCastMaze-/assets/146497900/f4c92d67-7f2d-4bd2-b760-e80f165cf3c0

---

## Technical Overview

### Maze Generation

The maze is procedurally generated using a random walk algorithm. The game initializes a grid of random colors, with each grid point representing a potential wall or open path. The random walk carves out a path through the maze, eventually creating an exit point. The random walk ensures that there is always a solution from the start to the exit.

- **Random Walk**: 
  - The algorithm starts at a random position in the maze.
  - It moves randomly in either the x or y direction, carving out a path by setting the grid cells to zero (indicating an open path).
  - This process continues until the exit is reached.

### 2D Ray Casting

The game uses 2D ray casting to simulate a 3D environment. Rays are cast from the player's position in small angular increments (forming a cone of vision). Each ray checks for collisions with walls in the maze, and the distance to the nearest wall is used to render vertical lines that simulate the height of walls in a 3D view.

- **Ray Casting Algorithm**:
  - Rays are cast in a loop, with each ray's angle calculated by adding a small offset to the player's current rotation.
  - For each ray, the position is incremented along the ray's direction (using sine and cosine) until a wall is hit or the ray leaves the maze bounds.
  - The distance of each ray is used to calculate the height of the wall slice that is rendered on the screen, with closer walls appearing taller and further walls appearing shorter.

### Rendering

The rendering process is handled using `matplotlib`. Horizontal and vertical lines are drawn to simulate walls, with heights calculated based on the distances from the player to the walls. The game renders a top and bottom portion of the screen, representing the sky and ground, respectively.

- **Rendering Mechanics**:
  - **Top Half**: Represents the sky and is drawn using light blue horizontal lines with a semi-transparent effect.
  - **Bottom Half**: Represents the ground and is drawn using gray horizontal lines.
  - **Wall Rendering**: Vertical lines are drawn for walls based on the distance from the player to the wall (calculated via ray casting). Colors are determined dynamically based on the type of wall hit (exit walls are rendered in blue, others in black).

### Player Movement

The player's movement is controlled via the keyboard. The player can rotate left or right and move forward or backward along the direction they are facing. The movement is smooth, and the ray cast field of vision updates in real time as the player moves through the maze.

- **Key Controls**:
  - **Up Arrow**: Move forward in the direction the player is facing.
  - **Down Arrow**: Move backward.
  - **Left Arrow**: Rotate left.
  - **Right Arrow**: Rotate right.
  - **Esc**: Exit the game.

### Procedural Generation and Exit Condition

The game ensures that the player always starts in a solvable maze with an exit point. The procedural generation creates unique mazes each time the game is played, and the game ends when the player reaches the exit point.

- **Procedural Maze**: Each maze is generated randomly, so the layout differs every time the game is played. The exit point is always reachable, ensuring that the game is solvable.
- **Exit Condition**: If the player reaches the exit tile, the game ends.

---

## How to Run the Game

1. Clone the repository:
   ```bash
   git clone https://github.com/colingalbraith/RayCastMaze-.git
