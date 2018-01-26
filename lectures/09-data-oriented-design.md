---
layout: page
active: lectures
title: "Lecture 9: Data-Oriented Design"
auto-title: true
---



[CppCon 2014: Mike Acton "Data-Oriented Design and C++"](https://www.youtube.com/watch?v=rX0ItVEVjHc)

> The purpose of all programs, and all parts of those programs, is to transform data from one form to another.
>
> If you don't understand the data, you don't understand the problem.
>
-- Mike Acton

There's essentially two core principles of DOD:

1. You need to understand the data to understand your software system - so design around the data.
2. There is never "one" of anything important - so design around the "multiple" case, not the single case.

Mike say something similar to what Bob Martin says about classes.
Another good example to consider:
In the real world, chairs are all similar to other chairs.
In a game, you might have a variety of chair classes -
`physicsChair`, `breakableChair`, `staticChair`.
In your engine code, these objects have almost nothing in common,
so having them all inherit from `Chair` is a bad idea.

The problem with OOP is that it organizes the data of your program based on this abstract, real-world influenced model of your system.
But at the fundamental level, what we're doing is transforming data in ways that you likely have some understanding of.
Your rendering pipeline transforms data about scene objects into gpu-ready serialized data into render calls.
Your physics system (or collision detection system) transforms a list of positions and other data into a list of new positions and other data.
If you think of this as a pipeline from physics, to scene/render, to OpenGL, it becomes clear that that's what's going on.

One problem with OOD is that it isolates the data involved in various operations.
We usually do things one at a time - update physics, animate, render.
Yet we take the data for those operations and spread it all over memory.
This in turns makes systems where it can be difficult to reason about what is being updated when,
what data is involved in which operations,
and what the exact steps to perform an update are.

Consider this node class that we might use as the base class for every object in our scene:

```cpp
class Node
{
public:
  void UpdateCollision();
  void UpdateAnimations();
  void Draw();

protected:
  Collision * m_Collision;
  vector<Animation *> m_Animations;

  mat4 m_Transform;
  mat4 m_AbsoluteTransform;
  vector<Node *> m_Children;
  Node * m_Parent;

  bool m_NeedsUpdate;

  MeshData * m_MeshData;
  Shader * m_Shader;
  vector<Texture *> m_Textures;
};
```
