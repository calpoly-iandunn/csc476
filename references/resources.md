---
layout: page
active: references
title: "Resources"
auto-title: true
---


## Mandatory

Mandatory?

[GLM](https://glm.g-truc.net/) - Math library.

[GLFW](http://www.glfw.org/) - Windowing and input abstraction layer.

[GLAD](http://glad.dav1d.de/) - OpenGL extension loading (simplest).

[CMake](https://cmake.org/) - C++ build platform.

[imgui](https://github.com/ocornut/imgui) - Awesome GUI library.






## Libraries

### Formats

#### [tinyobjloader](https://github.com/syoyo/tinyobjloader)

You might want to use `v0.9.25`.
Somewhat annoying interface changes in `v1.0.0`.

#### [assimp](http://assimp.sourceforge.net/)

Need to load something other than an `.obj`?
This loads (and exports) a lot of things.
A little bit of a pain to extract data.
Probably necessary for skinned meshes.



### General

#### [stb](https://github.com/nothings/stb)

This set of single-header C/C++ libraries is awesome because they provide lots of basic functionality without any of the standard adding-a-library-dependency-to-your-project headache.
You should never spend two weeks trying to get DevIL to compile on all of your development machines when stb_image.h exists.

  - Probably the most relevant are:
    - [stb_image.h](https://github.com/nothings/stb/blob/master/stb_image.h) (everyone will need this)
    - [stb_easy_font.h](https://github.com/nothings/stb/blob/master/stb_easy_font.h) (font rendering is a pain - only rely on this if you're not using imgui though)
    - [stb_perlin.h](https://github.com/nothings/stb/blob/master/stb_perlin.h) (procedural generation is fun)

#### [catch2](https://github.com/catchorg/Catch2)

Unit tests are the real deal. Just because it's game development doesn't mean you don't need these :) Catch is an awesome and minimal testing framework.
If some component in your game is just not working, refactor it to a class, make some mock objects, and write unit tests to figure out what is going wrong.
It's a lot better than spending eight weeks saying "don't do that because it breaks everything for some reason".



### GUI

#### [Dear imgui](https://github.com/ocornut/imgui)

The OpenGL GUI library ecosystem is a mess, and this is the only really good option.
Note that it is geared towards development UIs and is awesome at doing that.
If you want something that you can artistically control, you'll need to look elsewhere.

For production (pretty, user-centric) UI, I recommend just drawing textured quads.
As long as you don't need anything more complicated than buttons, progress bars, text, and static images, you'll be far better off just writing these yourself than trudging through the tepid mire of OpenGL GUI libraries.

#### [GWEN](https://github.com/garrynewman/GWEN)

If you really insist on using a GUI library that you can skin, GWEN is your best bet.
Last I checked, documentation was entirely non-existent for this library.
You will need to rely on your IDE for completions/intellisense.



### Animation

#### [Interpolation Functions](https://gist.github.com/iondune/11339413)

Interpolation can go a long way in terms of making things look and feel nice in your game.
Use these interpolation functions (especially the cubic ones if you can).



### Physics

#### [bullet3](https://github.com/bulletphysics/bullet3)

Great open source physics engine.
There website system is in flux and a total mess right now.
But it's a good library.

#### [PhysX](https://developer.nvidia.com/physx-sdk)

Industry proven.
Tons of features.
Very accessible.

#### [Havok](https://www.havok.com/)

Industry proven, commonly used.
Maybe not super accessible (last time I checked).



### Networking

Don't make a networked game in 10 weeks.

But if you must, read the [Game Networking](http://gafferongames.com/networking-for-game-programmers/)
and [Networked Physics](http://gafferongames.com/networked-physics/introduction-to-networked-physics/)
articles by [Gaffer on Games](http://gafferongames.com/).




## Interesting Reads

### Effects

#### [FXAA](http://blog.codinghorror.com/fast-approximate-anti-aliasing-fxaa/)

FXAA is great because it's a simple shader you can throw into your game as a one-pass post processing effect.

[I use a slightly modified version of this WebGL implementation in my engine.](https://github.com/mattdesl/glsl-fxaa)

#### [Outdoor Lighting](http://iquilezles.org/www/articles/outdoorslighting/outdoorslighting.htm)

Great article on how to do realistic lighting for an outdoor scene, especially terrain.

#### [Multiresolution Ambient Occlusion](http://iquilezles.org/www/articles/multiresaocc/multiresaocc.htm)

High level article on how to produce a convincing AO effect.
The author is writing from a procedural generation and offline rendering viewpoint, but the ideas are still useful for realtime.



### Other

[Semantic Versioning](https://semver.org/)


