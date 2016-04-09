---
layout: post
title:  "Quadrotor, and its physics, PART 2"
date:   2016-04-09 16:30:00 +0800
categories: quadrotor, quadcopter
---
So what is the Newton-Euler equation and how does it apply to motion planning?

It is a way of representing the __surrounding forces and torques on a rigid body__.
When the center of mass is at the origin of the reference frame, we are able to represent them in the following form (consisting matrices):  
(F)= (mI<sub>3</sub> 0 )(a<sub>cm</sub>) + ( &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; )  
(τ) &nbsp;&nbsp;&nbsp;(&nbsp;0 &nbsp;I<sub>cm</sub>)( α ) &nbsp;&nbsp;&nbsp;&nbsp;(ω x I<sub>cm</sub>ω)

where   
F is the force acting on the center of mass  
τ is the torque acting about the center of mass  
m is the mass of the rigid body  
I<sub>cm</sub> is the moment of inertia about the center of mass  
a<sub>cm</sub> is the acceleration of the center of mass
α is the angular acceleration of the rigid body  
ω is the angular velocity of the rigid body

__Equilibrium__
We are particularly concerned with the equilibrium state for quadcopters (duh!). An equilibrium state can be:
- Stable
- Unstable
- Critically stable

By using the following representations, we are able to calculate if a body is in equilibrium or not:
- q, the configuration/position of the system
- x, the state of the system
