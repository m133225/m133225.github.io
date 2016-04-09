---
layout: post
title:  "Search algorithms in Motion Planning"
date:   2016-04-09 20:30:00 +0800
categories: algorithms, A*, JPS
---
Maybe that was too much focus on the physics. Have to brush up on my physics before looking really in-depth into them. I shall study the algorithms side of it instead (which is the actual motion planning) :p

<hr/>

Before even attempting to search, we have to _model_ the environment somehow, so that the robot/algorithm knows which areas are to be avoided.

Let us focus on the 2D problem for now (an agent moving in a maze)

So how do we model a 2D space?
The main technique commonly used is __cellular decomposition__.
In other words, break down the space into cells (or grids).
Doing this will result in 3 types of cells:
- Completely blocked
  - Basically, obstacle occupied the whole cell
- Partially blocked
  - Cell is half-occupied by an obstacle
- Empty
  - No obstruction

Completely blocked cells and empty cells are rather straight-forward: allow/disallow traversals.
But what about partially blocked cells?
There are pros and cons of the different ways of handling them.
1. We make them traversable
  - obviously, this may not work since there is an obstacle
2. We make them not traversable
  - this may lead to incomplete search

Also, we can always increase the _resolution_ of the grids i.e. decompose each cell into even smaller cells
-> but this requires additional memory and computation, which may not always be feasible.

Similar concepts can be applied to 3D space, where we can model the environment with 3-dimensional grids.

__Note that when we model a 2D environment by grids, they are considered to be an 8-connected (if we allow diagonals) graph.__

Now to the actual motion planning!  
Which (real-time) grid-search algorithms can we use to find a path to the destination?

We can always rely on our old-school Breadth-First Search and Depth-First Search or even Dijkstra's algorithm.
A\* search is still better (complete, optimal and fast to compute given good heuristics) than them, in particular, a variation named __Jump Point Search__.  
It works similarly to A\*, except that it avoids checking for symmetrical paths. The basic idea is that it ignores grid that can be reached by its parent node with a cheaper cost.  
<a href="http://zerowidth.com/2013/05/05/jump-point-search-explained.html">Here</a> is an detailed explanation for JPS (with a customisable example!)

Note that it can perform more than 10x the speed of A\*!
