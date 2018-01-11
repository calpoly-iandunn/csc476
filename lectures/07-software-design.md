---
layout: page
active: lectures
title: "Lecture 7: Software Design"
auto-title: true
---


<a href="https://docs.google.com/presentation/d/10qUs3HXhfZMF6fia7hmKYRAJU4jUfSal0slutLOotLI/edit?usp=sharing" class="btn btn-info">Slide Deck</a>


One of the central ideas of this class is that we don't have enough time.
Games are complicated to make, so we're trying to keep our ideas as simple as possible,
and we're preparing to spend a lot of time coding.

When we're trying to move as fast as possible, it might seem like anything non-essential that takes up time should be ignored, in particular:

- Documentation
- Design Patterns and anything else that makes our code cleaner and longer
- Testing

These are things that waste time:

- **Uncertainty** within the team about what is done, what needs to be done, and how things should be done.
  Documentation can be used to address this.

- **Wasted effort** on features that end up needing to change or be removed to allow for other features.
  Planning ahead can only go so far in addressing this.
  Designing code to be as modular as possible can make it easier to pivot.

- **Difficulty** in adding new features and changing how old features work, due to interconnected dependencies within the codebase.
  Design patterns can be used to address this.

- **Frustration** at trying to solve a bug that is difficult to reproduce, and which could be caused by any number of components.
  Unit tests can be used to address this.



Things to consider:

- Side effects/mutation
- Clean Code
- Expressiveness

<!-- https://www.youtube.com/watch?v=TMuno5RZNeE - SOLID principles of design -->

<!-- Anything from *Clean Code* ? -->


## Working In Silos

- Relic Example
