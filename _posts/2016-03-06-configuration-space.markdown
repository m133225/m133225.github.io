---
layout: post
title:  "Useful tools for manipulating space representations"
date:   2016-03-21 01:00:00 +0800
categories: matrices, transformations
---
Just some additional background info (of me), I have learnt some Machine Learning algorithms, and am currently taking an
Introduction to Artificial Intelligence module. With interest in Motion Planning and Robotics, this is an exploration
of techniques outside the basic ones, so the pace might be slow :p

Moving on...

I have found a good [course materials](https://alliance.seas.upenn.edu/~meam620/wiki/index.php?n=Main.Schedule) for learning robotics. It seems to be very closely linked to motion planning.
Over the next couple of weeks. I will be reading through these course materials and studying them in-depth.

Before beginning to go in-depth into the topic of motion planning itself, we will need to start with representing positions in the 3D space.

Just some revision and definitions on 3D space before the real thing.  
(This is covered in the transformation slides)
***

Any **reference frame** in the 3D space can be defined using 3 orthogonal/basis vectors.

_Transformation_ usually refers to the relationship between 2 reference frames of different rigid bodies.
_Displacement_ usually refers to the relationship between 2 reference frames of the SAME rigid body.

So what is **rigid body displacement**?
- Transformation `g` of all points of a body
- Within the body itself:
 - any 2 points still have the same distance
 - any 2 vectors (formed by the 2 same points) will have the same cross product

**Rotational matrices**  
Rotational Matrix <sup>A</sup>R<sub>B</sub>
  - Transform from points wrt frame B to points wrt frame A  
Note that this does not account for displacement between the frames, only the rotation

Features of that we should take note:  
- the set of rotational matrices is a closed group (under multiplication)
 - product/inverse of a rotational matrix is another rotation matrix
- rotating the frame itself -> post-multiply
- rotating a position -> pre-multiply

**Transformations**
- Homogenous
 - Represents a rigid body transformation
 - It is in the form  
[R d]  
[0 1]  
where R is the rotational matrix, and d is the displacement matrix
 - basically 'increasing' the dimension for multiplication
- Composite
 - left-to-right transformation in the current frame
 - right-to-left transformation in the original frame
- Inverse  
 - It is in the form  
[Rt -Rtd]  
[0 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1 ]
***

It seems like we will be another 3 topics related to the physics/math side of it, before we move on to the actual motion planning itself. So brace yourselves :D
