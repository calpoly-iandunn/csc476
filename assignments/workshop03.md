---
layout: assignment
assignment: "workshop03"
title: SSAO Workshop
---


For this workshop, everything we need to do is in the `ssao_frag.glsl` fragment shader.

When you first open up the base code, it will:

1. Render a simple scene with four different meshes
2. Use a gbuffer FBO to save the color, normals, and depth of the scene into three textures.
3. Render a quad with the **SSAO** shader that includes debug modes for displaying color, normals, and depth.

It also sets up two things we will need for SSAO:

1. A set of random hemisphere samples with distance-weighted distribution
2. A set of random 2D vectors that can be used to rotate our hemisphere samples (and prevent banding)

To implement SSAO, we need to calculate and occlusion factor and multiple the scene colors by it.



## Step 1. Implement `reconstructViewspacePosition`

To do this we need a way to get viewspace positions from a depth value and $$x, y$$ location on the screen.
There are more optimized ways of doing this, but this is (I think) the most straightforward way to do it.

Sample $$ d $$ depth value from the depth texture.

Rescale both that and the $$ x, y $$ texture coordinates to 0 to 1 range.

$$ ndc = \{x, y, d\} * 2 - 1 $$

Compute viewspace using the inverse Projection matrix.

$$ vs = P^{-1} * \{ndc, 1\} $$

Finally, do the homogenous divide (since we used a Projection matrix).

$$ vs.xyz / vs.w $$



## Step 2. Implement `viewspaceToNDC`

We also need a way to get from viewspace to normalized-device-coordinates.

This is because we need to be able to sample the depth texture at some arbitrary place in viewspace,
and the x and y component of ndc can be easily scaled to texture coordinates for the depth texture.

1. Create a `vec4` with homogenous coordinate 1
2. Transform with `P` projection matrix (to get clip space)
3. Divide `clip.xyz` by `clip.w` (the homogenous divide) to get ndc
4. While we're at it, let's just scale it in 0 to 1



## Step 3. Sample Depth Values!

Now we have the tools we need to implement a simple and broken SSAO function.

1. Calculate the fragment position in view space.
2. Loop over our pre-computed hemisphere samples.
3. Add the hemisphere sample vector to the fragment position to get a viewspace sample position.
4. Reconstruct a viewspace position from the gbuffer (depth buffer)
5. Check which is closer to the camera - the sample location or the reconstructed position

The reconstructed position represents geometry in the scene.
So if the reconstructed position is closer than the sample point, our sample is occluded.
Count the occluded samples, and that becomes an occlusion factor!

This will look very bad.



## Step 4. Transform Samples Out of Tangent Space

Our hemisphere sample vectors are in tangent space, so this is only going to look OK for surfaces facing the camera.

We need to transform our sample vectors out of tangent space and into view space.
This can be done using a **TBN** matrix, just like you would use for normal mapping.

However, a TBN matrix needs tangent vectors to compute.
We don't have tangent vectors (and we actually don't want the UV space tangents).
We want to pick a random tangent vector so that each fragment has a randomly rotated hemisphere.

This is where the noise texture we generated comes into play.


```glsl
// Random vector (to orient hemisphere)
vec2 noiseScale = vec2(textureSize(sceneDepthTex, 0)) / textureSize(noiseTex, 0);
vec3 randomVec = vec3(texture(noiseTex, texCoord * noiseScale).xy, 0.0);
```

Okay, but how do we make a set of basis vectors from a normal and a random vector?
Using the [Graham-Schmidt Process](https://en.wikipedia.org/wiki/Gram%E2%80%93Schmidt_process)!

That wikipedia article is really indecipherable (just overly general).
Think of it this way: we want a set of set of orthogonal basis vectors, and we just have two vectors that may not be orthogonal.
So how do we make them orthogonal?

Project the second vector on to the first, then subtract that from the second vector.
We just removed from the second vector any part that is pointing in the same direction as the first vector.
Normalize, and you've got two orthogonal vectors.

```glsl
// Tangent to view transform
vec3 tangent = normalize(randomVec - normal * dot(randomVec, normal));
vec3 bitangent = cross(normal, tangent);
mat3 TBN = mat3(tangent, bitangent, normal);
```

Now we just need to use this `TBN` matrix on our sample vectors to get sample vectors in view space, and the image should look a lot better.



## Step 5. Range Check

Right now we're not checking whether a sample vector is occluded by nearby geometry or just any geometry at all.
This is given shadowy outlines to everything in the scene that's in front of something else.
We can fix this by only considering a sample occluded if the distance between the sample and reconstructed points (in z) is less than our hemisphere radius.



## Step 6. Blur

We should blur this to make it look less noisy, but that is left as an exercise for the reader :-)

