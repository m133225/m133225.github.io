---
layout: post
title:  "Rotations, and how they are represented"
date:   2016-03-23 11:49:00 +0800
categories: matrices, rotations
---
So let's move on to rotations.
<hr/>
There is a group of rotations, called Special Orthogonal group SO(n) where n is the dimension of the issue. This is also known as the _lie_ group.

There are several representations for these group of rotations which we will be discussing later on.

The SO(3) group satisfies 4 axioms: closure, associativity, identity and invertibility. In addition, it is also considered a continuous group since the binary operator is a continuous operation. It is also a _smooth manifold_, which we will look into now.

**Manifolds**  
So what are _smooth manifolds_?  
First, let's look at the ideas of _homeomorphism_ and _diffeomorphism_.  

Basically, _homeomorphism_ is a function that maps one topological space to another, with the following properties:

- Bijection
- f and f<sup>-1</sup> are both continuous

_Diffeomorphism_, on the other hand, is a function f, together with its inverse f<sup>-1</sup>,

- has all partial derivatives, of all orders
- which all partial derivatives are continuous

So, then, a _manifold_ (of dimension n) is a set M which is homeomorphic to R<sup>n</sup>.
For it to be a _smooth manifold_, it should ALSO be _locally diffeomorphic_ to R<sup>n</sup>

**Euler Angles**

Another way to represent a rotation is through the use of _Euler angles_. Basically, any rotation in a 3D space can be represented as a combination of 3 rotations about linearly independent axes.
The rotation of the y-axis should be between 0 or pi, unless the axes are not linearly independent in the first place.

While Euler angles are easy to understand, they have duplicate ways of representing the same rotation.

**3D Rotation Matrices**  
The Euler's Rotation Theorem  
- Displacement of rigid body such that one of its points remains fixed, is equivalent to a rotation

The proof is explained rather detailedly in [Wikipedia](https://en.wikipedia.org/wiki/Euler%27s_rotation_theorem)

This theorem is essential in deriving the Rodrigue's rotation formula, which helps us to combine the 3 axis-angle rotations without having to compute them explicitly (which is intensive).  
𝐑<sub>𝐮,𝜙</sub> = 𝐈cos𝜙 + 𝐮𝐮<sup>𝑇</sup>(1 − cos𝜙) +𝐮sin𝜙  
where u is the unit vector of the rotation axis, and 𝜙 is the angle rotated according to the right hand rule.
