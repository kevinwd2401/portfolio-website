---
title: "Real-Time Physically-Based Shaders"

tags:
  - C++
  - OpenGL
  - GLSL
---

|![](/images/projects/gi_example.png)|![](/images/projects/gi_example2.png)|
|:---:|:---:|

This shading model was implemented as part of our Advanced Rendering class, based on the real-time shading model used in [Unreal Engine 4](https://cdn2.unrealengine.com/Resources/files/2013SiggraphPresentationsNotes-26915738.pdf). 

In our fragment shader, we implement the Torrance-Sparrow microfacet model, using approximations such as the Schlick’s approximation for fresnel term and Schlick-GGX for geometric attenuation. For image-based lighting, we precompute the diffuse and glossy irradiance with different blur thresholds via mipmaps and store it in cube textures for sampling. Also implmented are normal/displacement maps and albedo maps.

We then modified the pipeline to support deferred rendering to add screen-space reflections. Reflections are progressively blurred and sampled based on the reflective material's roughness.

![](/images/projects/ssr_example.png)