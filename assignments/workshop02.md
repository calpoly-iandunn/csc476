---
layout: assignment
assignment: "workshop02"
title: Shadow Workshop
---


How things start:

![shadows-1](shadows-1.png){:class="img-thumbnail"}


## Task 1:

Set up the transforms to be able to "draw from the light" - edit:

Fill in `SetLightView` and `SetOrthoMatrix` with reasonable values and send the matrices to the appropriate shaders.



## Task 2:

Once you get the transforms in place - make sure your matrices are right.

First, get the geometric debug to show your scene from the light's perspective to work.
In the base code `SHOW_LIGHT_COLOR` can be set to `true` to show the colors of the scene from the light camera's view.
Hold the **`L`** key to toggle `SHOW_LIGHT_COLOR`.

There are two shaders used for this debug view: `depth_vertDebug.glsl` and `depth_fragDebug.glsl`.
Correct output should look something like the image below, except with texture colors visible:

![shadows-2](shadows-2.png){:class="img-thumbnail"}



## Task 3:

`SHOW_LIGHT_DEPTH` can be used to display the depths of the scene as rendered from the light's perspective.
Hold the **`K`** key to toggle `SHOW_LIGHT_DEPTH`.
There are depth debug shaders: `pass_vert.glsl` and `pass_texfrag.glsl` ("DebugProg"),
that will draw a large quad and texture map on the depth map.
When the light depth's map view to work, it should look something like:

![shadows-3](shadows-3.png){:class="img-thumbnail"}



## Task 4:

Now that we have the shadow depth rendered, we need to use this information to shade the objects.

First, we need to do some setup in `main.cpp`:

1. In `render()`, provide the shadow map texture to the scene draw call.

2. Also provide the light matrix.

To complete the shadow mapping, you need to edit the final pair of shaders

1. Edit `shadow_vert.glsl` to transform the point into Light space per vertex (hint: what matrix do you need)

2. Edit `shadow_frag.glsl` to complete the shadow depth test:
   1. shift the coordinates from $$ \{-1, 1\} $$ to $$ \{0, 1\} $$
   2. read off the stored depth (`.`) from the ShadowDepth, using the shifted.xy
   3. compare to the current depth (`.z`) of the projected depth
   4. return $$1$$ if the point is shadowed

You can also implement percentage closer shadows, which blend neighboring depth values to scale shadow intensity.

Final shadow mapped look:

![shadows-4](shadows-4.png){:class="img-thumbnail"}

