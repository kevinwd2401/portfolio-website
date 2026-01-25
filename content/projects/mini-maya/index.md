---
title: "Mini-Maya"

tags:
  - C++
  - OpenGL
  - GLSL
---

![](/images/projects/cow_mesh.png)

I developed a basic mesh editor that replicates core functionality found in modern 3D modeling software. The editor is built around a half-edge data structure, which is what many widely used modeling tools are based on. Through the interface, users can load _.obj_ files and directly manipulate mesh vertices. Supported operations include Catmull–Clark subdivision, face triangulation, edge splitting, and face extrusion.