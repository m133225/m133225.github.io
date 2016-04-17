---
layout: post
title:  "Quadrotor, and its physics, PART 1"
date:   2016-04-05 20:30:00 +0800
categories: quadrotor, quadcopter
---

Now that we have looked at basic representations of the 3D space, we can move on to something more complex: the physics of quadcopters.

__Newton-Euler Equations__  
Newton-Euler equations are an extension of Euler's law of motions, which are in turn extensions of Newton's law of motion. They are ways to represent the translations and rotations of a rigid body.

So let's start with Euler's law of motion since Newton's law of motion should be familiar to most science students. (not me, however).

First off, let's begin with __Euler's first law__.
It states that the linear momentum of a body is equal to mass of the body times the velocity of the body's center of the mass.  
In order words:  
p = mv<sub>cm</sub>  
where p is the linear momentum of a body, m is the mass of the body, v<sub>cm</sub> is the velocity of the body's center of the mass.

Proceeding on to __Euler's second law__.
It states that the rate of change of the angular momentum at a point is equal to the sum of external moments of force acting on the body:  
M = dL/dt

Newton-Euler equations also make use of principal axes and moments.  
__Principal axis of inertia__  
- a vector u is considered to be along a principal axis if Iu is parallel to u, where I is the inertia of the rigid body  
__Principal moment of inertia__  
- moment of inertia with respect to a principle axis is called a principal moment of inertia

That's all the physics to read through for now. In the next post, we will be looking at how to combine these laws into Newton-Euler equations.
