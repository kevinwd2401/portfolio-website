---
title: "Monte Carlo Path Tracer"

tags:
  - C++
  - OpenGL
  - GLSL
---

This Monte Carlo path tracer is implemented in GLSL, with the majority of computation performed on the GPU. The renderer draws on concepts from *Physically Based Rendering* and casts rays per fragment from the camera through each pixel, simulating multiple light bounces. At each bounce, direct light sampling is weighted and contributes to the overall radiance.

The path tracer implements image-based environment lighting for global illumination, different types of lights and materials/BDSFs, and uses multiple importance sampling to improve convergence speed and reduce noise.


|![](/images/projects/KevinDu_RoughMirrorEnv.png)|![](/images/projects/KevinDu_NoLightEnv.png)|
|:---:|:---:|
|Cornell Box|Cornell Box, evironment light only|

|![](/images/projects/KevinDu_Spotlight.png)|![](/images/projects/KevinDu_StackedShapes.png)|
|:---:|:---:|
|Spotlight|Different BSDFs|

|![](/images/projects/KevinDu_GlassBoxes.png)|![](/images/projects/KevinDu_CustomMirrorBox.png)|
|:---:|:---:|
|Neon and Glass Boxes|Portals and Mirrors|
