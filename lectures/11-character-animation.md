---
layout: page
active: lectures
title: "Lecture 11: Character Animation"
auto-title: true
---


<a href="https://docs.google.com/presentation/d/1kpt6oyzqrPBA2e3MvSqC-ioQsuWYg2DdfmdEDiTNNt8/edit?usp=sharing" class="btn btn-info">Slide Deck</a>



How do we animate?

Modifying scene parameters as a function of time.

## Scripting

Specifiying the parameters at every frame.

```python
define spinningCube()
  rotAngle = pi*frameNumber / 50
```

```python
define carScript()
   carTranslation = 10*(frameNumber / 100)
   wheelRotation  = pi*frameNumber / 5
```

### Hierarchical Modeling

<div id="example1">
  <iframe id="exampleFrame1" src="11-example-hierarchical.html" width="820px" height="420px"></iframe>
</div>

This is the order you typically apply rotations:

$$ T * R * S $$

Why?

* Non-uniform scale will mess up rotations
* Translation will mess up everything

In a hierarchical model, generally do T and R, then `push()` for S, draw, and `pop()` before continuing on.
Unless your models are positioned with the origin at where you want it to pivot, you typically also need to do a translate after the rotate but before the scale (because translates mess up everything).

Here's the (simplified) javascript code for the above example.


```js
push(); // upper-arm rectangle (red)

  rotate(upperArmRotation);
  drawAnchor();
  push();
    translate(100, 0);
    drawRect(200, 100); // box
  pop();

  push(); // lower-arm rectangle (green)

    translate(200, 0);
    rotate(lowerArmRotation);
    drawAnchor();
    push();
      translate(100, 0);
      drawRect(200, 80); // box
    pop();

    push(); // hand rectangle (blue)

      translate(200, 0);
      rotate(handRotation);
      drawAnchor();
      push();
        translate(75, 0);
        drawRect(150, 60); // box
      pop();

    pop();

  pop();

pop();
```

The boxes we draw are *centered* at the origin, so we need to translate out $$1/2$$ the width to get the pivots/anchors we want.


## Key-Framing

**Key-framing** means defining specific animation frames and interpolating between them to get frame-by-frame animation poses.
Typically an artist creates the keyframes.

But how do we interpolate the poses?
Can we just use linear interpolation?

For poses $$ p_0 $$ and $$ p_1 $$ and $$ t $$, which goes from 0 for pose 0 and to 1 for pose 1.

$$ p = p_0 * (1 - t) + p_1 * t $$

- For positions? Absolutely?
- Scales? Yes.
- Rotations? Nope.

### Rotation Interpolation

Well, there wouldn't be a section here if it wasn't possible.
But the familiar methods of rotation representation will not work!
What are those methods?

* Euler angles
* Rotation matrix

Euler angles absolutely won't work and will look bad (not constant angular velocity).
Euler angles are also also susceptible to gimbal lock.
Rotation matrices have basically the same problem with regard to interpolation.
It can be solved but is math heavy.

However, there is a rotational representation that has a simple way to interpolate!
It's called quaternions.

### Quaternions - Simple Mode

Quaternions can be used to represent a rotation.
And they're in glm!

You can make a quaternion from Euler angles:

```cpp
glm::quat q = glm::quat(euler);
```

And from a rotation matrix:

```cpp
glm::quat q = glm::quat(matrix);
```

And you can easily [interpolated between two quaternions](https://glm.g-truc.net/0.9.0/api/a00135.html#a99e0097254662e3d4d5859fa329762ca):

```cpp
glm::quat q = glm::gtx::quaternion::mix(q0, g1, 0.5f);
```

And finally, you can get a rotation matrix back from the quaternion:

```cpp
glm::mat4 m = glm::gtc::quaternion::mat4_cast(q);
```



### Quaternions - Math Mode

#### Complex Numbers

Recall, complex numbers:

$$ (a, b) = a + b i $$

$$ a $$ is a real number.

$$ i $$ is an imaginary number.

It has some interesting rules: $$ i^2 = -1 $$

So we can multiply two complex numbers following the rules of algebra:

$$ (a + b i) * (c + d i) = $$

$$ a * c + a * d i + b i * c + b i * d i = $$

$$ ac + ad i + bc i + bd i^2 = $$

$$ (ac - bd) + (ad + bc) i $$

We can also write this:

$$ (a, b) * (c, d) = (ac - bd, ad + bc) $$

Alright, what else can we do with complex numbers?
We can plot them in 2D.

![complex-number](11-figure-complex-number.png){:class="img-thumbnail"}

Doing so shows us a few interesting aspects of complex numbers:

* If we multiply by $$ i $$, the number rotates around 90 degrees.
* If we multiply by $$ -1 = i^2 $$, the number rotates around 180 degrees.

What if we multiply by any other unit-length complex number?

$$ (a, b) * (cos\theta, sin\theta) = (a cos\theta - b sin\theta, a sin\theta + b cos\theta) $$

But wait! This looks like...

$$ \begin{bmatrix}cos \theta & -sin \theta\\sin \theta & cos \theta\end{bmatrix} \begin{bmatrix}a\\b\end{bmatrix} = $$

$$ \begin{bmatrix}a cos\theta - b sin\theta\\a sin\theta + b cos\theta\end{bmatrix} $$

Because it is.

#### What about 3D?

This is rotation around a **single axis**, and we need **two** numbers to do it - a real and imaginary part.

We also use *unit-length* complex numbers, not just all of them.

To represent a 3D rotation, with is around **three axis**, we need **four** numbers to do it - a real and three imaginary parts.

[Euler's rotation theorem](https://en.wikipedia.org/wiki/Euler%27s_rotation_theorem) tells us that we can represent any arbitrary rotation in 3D
as a rotation around a single axis $$ \vec e $$ by a given rotation $$ \theta $$.

So we need exactly **four numbers** to describe an arbitrary rotation.
This makes sense!
(I hope).

#### Quaternions

Okay so what is this set of four numbers, three of which are imaginary?

$$ i^2 = j^2 = k^2 = ijk = -1 $$

$$ ij = k $$ and $$ jk = i $$ and $$ ki = j $$

$$ ji = -k $$ and $$ kj = -i $$ and $$ ik = -j $$

This forms an extended version of the complex numbers:

$$ w + xi + yj + zk $$

We can write the coordinates this way:

$$ (w, x, y, z) $$

Or as a scalar and vector pair:

$$ (w, \vec v) $$

How can we represent a rotation with this?

$$ w = cos(\frac{\theta}{2}) $$

$$ (x, y, z) = \vec v = sin(\frac{\theta}{2} \hat r) $$


---



## Outline

1. Forward Kinematics/Key framing
1. Inverse Kinematics
1. Motion capture
1. Simulation
  1. Behavioral Animation
  1. Physically based (Dynamics)



- Key framing
- Interpolation
- Rotations
  - Euler angles
  - Quaternions
- Splines
- Skinning
- Kinematics
- Inverse kinematics
- Motion capture
- Collision detection
  - Spatial data structures
- Principles of animation
  - Squash and stretch
  - Timing and motion
  - Anticipation
  - Follow through
  - Arcs
  - Ease in/out
