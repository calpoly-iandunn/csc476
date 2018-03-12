---
layout: assignment
assignment: "workshop04"
title: Deferred Shading Workshop
---


Base Code
---------

When you run the base code, you should see some diffuse shaded spheres moving around slowly.

The base code is rendering a scene into a G-Buffer, then doing a light pass.
However, there is no light code, so the lights are rendered as spheres (in the usual way).

- You can hold **`[H]`** to see the colors in the G-Buffer.
- You can hold **`[J]`** to see the normals in the G-Buffer.
- You can hold **`[K]`** to see the depth in the G-Buffer.
- You can hold **`[L]`** to see the reconstructed world-space positions from the G-Buffer.

All of the debug modes are implemented in `debug_frag.glsl`.

For this workshop, we need to implement all of the deferred shading in `light_frag.glsl`.
We'll also need to do some setup in `main.cpp` pertaining to the lighting pass.

### Light Volumes

![light volumes](deferred-shading-00.png){:class="img-thumbnail"}

### G-Buffer Colors

![g-buffer colors](deferred-shading-01.png){:class="img-thumbnail"}

### G-Buffer Normals

![g-buffer normals](deferred-shading-02.png){:class="img-thumbnail"}

### G-Buffer Depth

![g-buffer depth](deferred-shading-03.png){:class="img-thumbnail"}

### G-Buffer Positions

![g-buffer positions](deferred-shading-04.png){:class="img-thumbnail"}

