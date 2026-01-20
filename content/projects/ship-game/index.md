---
title: "Big Boat Battle"

tags:
  - Unity
  - C#
  - HLSL
  - Shadergraph
  - Houdini
---

![](/images/projects/ship_demo_gif.gif)

This my top-down combat game where you pilot a toy boat against waves of enemy ships within a foggy pool! Some interesting features include:

- **Volumetric Fog**, which can be parted by objects which attenuate the fog density
- **Procedural Water** with Ripples using render textures and a wave shader
- Render texture scrolling to follow the player across a potentially infinite map
- Boid NPC behaviors to create enemy ship formations
- Procedural behavior generation for enemies, with possible states depending on assigned tasks and enemy type
- **Procedural enemies**, with varying coloration, decoration, and armaments based on enemy types
- A variety of ships procedurally modelled in Houdini

|![](/images/projects/ship_closeup_crop.png)|![](/images/projects/boat_houdini.png)|
|:---:|:---:|
|In-game prototyping|Houdini modelling|

Demo Video: https://www.youtube.com/watch?v=cPxqBuK4olA


------
## Render Textures

|![](/images/projects/ship_ripple_tex.png)|![](/images/projects/waterboat.png)|
|:---:|:---:|
|Render Textures for Water Ripples|Fog Attenuation|


The **procedural water** is created using noise and sine waves displaced by time. To create the ripples, a top-down orthographic camera renders water-interacting objects to a collision render texture (RT) for wave creation. Next, an additive blend shader takes the current frame's wave RT and blends it with this collision RT. Lastly, a wave fragment shader reads current frame and previous frame wave RT, computing next frame's wave RT with simple propogation and damping. This render texture is sampled by the water shader and used to distort the normals.

For the **volumetric fog**, a top-down orthographic camera similarly renders fog-interacting objects to a collision render texture, before an additive blend shader blends it with the current frame's fog RT. The render texture is dampened every frame to simulate the fog filling the space back up, and this is read by the fog raymarcher for density attenuation.