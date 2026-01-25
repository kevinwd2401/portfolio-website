---
title: "Procedural Fireball"

tags:
  - TypeScript
  - OpenGL
  - GLSL
---

![](https://github.com/kevinwd2401/hw01-fireball/raw/master/fireball.png)

I create a procedural fireball with a shader in GLSL. We start by rendering a base sphere mesh, which is then deformed through stretching, tapering with bias and gain functions, and then oscillated with trig functions. 

The chaotic appearance is caused by radial displacement, driven by FBM Perlin noise scrolling upwards. Additional trig oscillations along the X and Z axes mimic a strong flame. The fragment shader applies discrete color banding, interpolated between two color parameters by FBM noise and then layered on top of a base color gradient.

I promise it looks a bit cooler in the Live Demo!

Live Demo Link: [_https://kevinwd2401.github.io/hw01-fireball/_](https://kevinwd2401.github.io/hw01-fireball/)