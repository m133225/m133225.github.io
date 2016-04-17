---
layout: post
title:  "Motion Planning for Multi-robot"
date:   2016-04-16 20:00:00 +0800
categories: algorithms A* multi-agent
---
In the previous post, we only discussed about the search for a single-agent.
Then what about planning for multi-agent robots? How do we make them work together in an optimal way?

Actually, we can simply reuse algorithms for single-agent in a multi-agent setting.
For example, let's consider planning for 2 robots (under the same multi-robot system).

We can take the _cartesian product_ of both graphs, remove the collision states, then use A* to plan paths.

While this is possible, the amount computation needed will increase exponentially, as the number of robots are increased.
This is known as the Curse of Dimensionality.

Let's look at a slightly different problem.
Instead of trying to make Robot A move to goal A and Robot B move to goal B and so on, we allow the robots to move to any of the goal, as long as all goals are visited.
We call this problem **CAPT - Concurrent Assignment and Planning of Trajectories**.
However, there is the problem of intersecting paths, which may result in collision.

There is a theorem to help us: Minimizing total distance will almost always result in non-intersecting paths.
So basically, we can minimize total distance in order to get a set of paths.
This is rather straight-forward: we emulate a table with the distance of each robot to the different goals. We then attempt to find an assignment such that it minimizes the total distance travelled. For this, we can use the [Hungarian algorithm](https://en.wikipedia.org/wiki/Hungarian_algorithm) which has a O(n<sup>3</sup>) running time.

However, if we add in an assumption, we can ensure that it will result in non-intersecting paths.
Assume that the distance between the starting points and the goal is larger than 2 x R x sqrt(2), where R is the radius of the (circular) robot.

However, when we add in obstacles, the above assumption will not hold. With intersecting paths, we then have to determine the priority order.
This can be done by checking if there will still be intersection between 2 robots if one of them does not move.

- If there is still intersecting paths, then the one that did not move will have a higher priority.
- If not, checking if there is still intersecting paths if the one that didn't move now moves (and completes) its path first. If there is, then the other one will have higher priority.

Let's summarize the above in simple steps for multi-agent planning:

1. Compute the shortest length paths (squared) from the robots to every goal
2. Find the best assignment using Hungarian algorithm
3. Determine the priority of intersecting paths.
4. Even after delegating the paths to the robots, it is still up to the robots to optimize its own trajectory to ensure that its path is safe & does not interfere with higher-priority robots.
