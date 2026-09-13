---
title: "Boid Simulation"

tags:
  - CUDA
  - C++
  - OpenGL
---

![Boid simulation](https://github.com/kevinwd2401/Fall2026-Project1-CUDA-Flocking/raw/main/images/boids_01.png)

|![Boid simulation animation](https://github.com/kevinwd2401/Fall2026-Project1-CUDA-Flocking/raw/main/images/boids_1.gif)|![Sprott attractor animation](https://github.com/kevinwd2401/Fall2026-Project1-CUDA-Flocking/raw/main/images/boids_sprott.gif)|
|:---:|:---:|
|Default simulation|Sprott attractor simulation|

## Overview

A group of individual boids can produce emergent flocking behavior just by following simple local rules: cohesion, separation, and alignment.

For each individual boid, the simulation performs the following pseudocode every frame:
```
for each nearby boid:
    if within cohesion radius:
        move toward the neighbors' average position
    if within separation radius:
        move away from nearby neighbors
    if within alignment radius:
        match the neighbors' average velocity

update velocity using the combined steering forces
limit the boid's speed
update position using the new velocity
```

## Implementation

- CUDA-based boid simulation with cohesion, separation, and alignment rules
- Naive brute-force neighbor search
- Scattered uniform-grid neighbor search using Thrust sorting
- Coherent uniform-grid neighbor search with position and velocity data reordered by grid cell
- CUDA kernels for:
  - Computing grid-cell indices
  - Sorting boids by grid cell
  - Reshuffling boid data into coherent memory order
  - Updating boid velocities and positions

An analysis comparing performance between different implementations, boid counts, and CUDA block sizes can be viewed on [**Github**](https://github.com/kevinwd2401/Fall2026-Project1-CUDA-Flocking).




![FPS by boid count without visualization](https://github.com/kevinwd2401/Fall2026-Project1-CUDA-Flocking/raw/main/images/boid_vs_fps_no_vis.png)


![FPS by CUDA block size](https://github.com/kevinwd2401/Fall2026-Project1-CUDA-Flocking/raw/main/images/block_size_vs_fps.png)

## Additional Experiments

I played around with strange-attractor vector fields which influence the boids' velocity updates. The vector field is evaluated at each boid's position and added to its acceleration, allowing the flock to form interesting patterns around attractors such as Lorenz, Thomas, Halvorsen, and Sprott B.

|![Lorenz attractor animation](https://github.com/kevinwd2401/Fall2026-Project1-CUDA-Flocking/raw/main/images/boids_lorenz.gif)|![Thomas attractor animation](https://github.com/kevinwd2401/Fall2026-Project1-CUDA-Flocking/raw/main/images/boids_thomas.gif)|
|:---:|:---:|
|Lorenz attractor|Thomas attractor|
