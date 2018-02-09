---
layout: assignment
assignment: "workshop01"
title: VFC Workshop
---

## Overview

The goal of this assignment is to implement a simple view-frustum-culling program.
The base code draws a simple scene with snowmen and Nefertiti models.
Using bounding spheres, we will individually cull each model that is outside the view frustum.

The base code also includes two top-down view of the scene - one with VFC enabled and one without.

Your task is to implement the stubbed VFC functions.



## Steps

### Step 1: Extract Frustum Planes

[Refer to this resource](http://gamedevs.org/uploads/fast-extraction-viewing-frustum-planes-from-world-view-projection-matrix.pdf)
for details on how to extract planes from a composite projection-view matrix.
Note that the article begins with an explanation for Direct3D -
skip over this to get to the OpenGL explanation (it's different because of the canonical view volume for each platform).

Your code should go in `ExtractVFPlanes`

### Step 2: Implement Cull Function

Now that we have our planes, we must use them to cull objects!

First, implement `DistToPlane` to return the distance from a point to a plane (signed distance - positive on one side and negative on the other).

Then, implement `ViewFrustCull` so that it returns 1 for any object outside of the frustum!



## Notes

### GLM Matrix Element Access

`glm mat4` has the `[]` operator overloaded so that you can access individual elements.
However, it confusing provides access to *columns*.
Also, it indexes from `0` (as it should) instead of from $$1$$ like the matrix resource.

So $$ m_{3, 1} $$ is equivalent to `m[0][2]` for us.


### Implicit Plane Equation

A plane is defined by a point $$p_1$$ and a normal $$\hat n$$.
The plane consists of all points for which $$(p-p_1)$$ is perpendicular to $$\hat n$$.

Or, using the dot product:

$$ f(p) = (p - p_1) \cdot \hat n = 0 $$

And to get the implicit equation:

$$ f(x, y, z) = (x - p_x) * n_x + (y - p_y) * n_y + (z - p_z) * n_z = 0 $$

$$ = n_x * x + n_y * y + n_z * z - (n_x * p_x + n_y * p_y + n_z * p_z) $$

$$ = A * x + B * y + C * z + D $$

where

$$ A = n_x $$

$$ B = n_y $$

$$ C = n_z $$

$$ D = - (n_x * p_x + n_y * p_y + n_z * p_z) $$

or

$$ \{A, B, C\} = \vec n $$

$$ D = - \vec n \cdot \vec p $$

The implicit equation gives us a way compute (signed) distances from a plane.
