---
layout: page
active: lectures
title: "Lecture 1: Graphics Pipeline Review"
auto-title: true
---


Graphics Pipeline Review
------------------------

{% include image-block.html file="01-figure-graphics-pipeline.png" alt="Graphics Pipeline" %}


**Object space:** the coordinates stored in the mesh file, uploaded to the VBO, and sent to vertex shader as `in vec3 vPosition`

**World space:** `M * vPosition`

**View space:** `V * M * vPosition`

**Clip space:** `P * V * M * vPosition`

**Normalized device coords:** `clip.xyz / clip.w`

**Window coords:** `gl_FragCoord`



Matrix & Vector Review
----------------------

- [471 Vectors Lecture](https://iondune.github.io/csc471/lectures/05-vectors)
- [471 Matrices Lecture](https://iondune.github.io/csc471/lectures/06-matrices)
- [471 Matrix Operations Lecture](https://iondune.github.io/csc471/lectures/07-matrix-operations)
- [471 Coordinate Transforms Lecture](https://iondune.github.io/csc471/lectures/08-transformations)
- [471 Matrix Transforms Lecture](https://iondune.github.io/csc471/lectures/12-geometric-transforms)
- [471 Hierarchical Transforms Lecture](https://iondune.github.io/csc471/lectures/13-hierarchical-modeling)

Who can tell me what's wrong with this code?

```cpp
glm::mat4 model, view, projection;
glm::vec4 pos  = glm::vec4(1.1, 3.2, 9.7, 1.0);

glm::vec4 worldSpacePos = pos * model;
```



GLSL Review
-----------

Who can tell me what this does?

```glsl
gl_Position = gl_Position.xyww;
```



Lighting and Shading Review
---------------------------

- [471 Color Vision Lecture](https://iondune.github.io/csc471/lectures/15-lighting-1)
- [471 Reflection Models Lecture](https://iondune.github.io/csc471/lectures/16-lighting-2)
- [471 Lighting and Shading Wrapup Lecture](https://iondune.github.io/csc471/lectures/17-lighting-3)

![blinn-phong reflectance model](01-figure-blinn-phong.png)

