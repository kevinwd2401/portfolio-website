---
title: "Mini Minecraft"

tags:
  - C++
  - OpenGL
  - GLSL
---


![](/images/projects/minecraft_landscape.png)

My team and I built a voxel game engine inspired by Minecraft, using C++ and GLSL. This experience taught me a lot about GPU rendering pipelines. My contributions include: 
- Procedural biome assets
- Procedural biome grass coloring
- Water waves and specular reflection
- Post-process camera overlay for water and lava
- Distance fog
- Player physics
- Procedural cave generation

### Procedural Assets
I created 3 procedural assets: normal trees, pine trees, and ice spikes. Their sizes and appearances sample their y-positions as an efficient way to obtain randomness. They are placed along the x-z-plane with poisson disk-sampling to keep them roughly evenly spaced within their chunk.

### Procedural Grass Coloring
Using the 2 Perlin noise functions which determine the biomes, I interpolate between multiple different grass colors in the lambert fragment shader for grass blocks.

### Water Waves
The water from the fragment shader is distorted using the sum of multiple sine waves. Using the partial derivatives of this sine function, I calculate the normals at each point and then use the current direction of the animated sun to add the specular highlights.

### Post-Processing
![](/images/projects/minecraft_water.png)
When in water and lava, I use a vignette, followed by a distortion the screen's UV coordinates with Perlin noise. For the water, I use a blue tint to make the screen appear desaturated, and I use a red tint with more Perlin noise when in lava to try to imitate the viscosity. When in lava, red-tinted distance fog is enabled to emulate the Minecraft lava’s opacity.
