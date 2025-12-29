---
layout: post
title: Let's learn Lagrange multipliers by hiking
categories:
- sbagleyteaches
---

So here's the problem: You want to optimize some function $ f(x, y)$ subject to the constraint $ g(x, y) = k$. The method of Lagrange multipliers says that you can do this by solving the equations $ \nabla f = \lambda \cdot \nabla g$. But wait, why?

Here's how I like to think about this. You're hiking on Mount Glass, a weird transparent mountain whose elevation above the "floor" is given by $ f(x, y)$. Down on the "floor", someone has painted a path given by the constraint $ g(x, y) = k$. You can look down through the mountain (because it's transparent) to the "floor" below to see where the path is drawn, and you can't leave the path -- your shadow always has to land right on the path painted on the floor. (It's noon, so your shadow just goes straight down.)

In this weird scenario, what's the highest you get?

To answer this question, we're going to exploit one of my favorite facts about the gradient vector: it points in the direction of fastest increase. In this context, that means that $ \nabla f$ is the vector that points straight up the hill from where you are standing right now. (Note that it does not necessarily point at the peak of Mount Glass!)

We're simultaneously going to exploit my *other* favorite fact about the gradient vector: it's perpendicular to level curves. (These two facts are equivalent.) In particular, it'll be useful to us to note that $ \nabla g$ is always perpendicular to our path, because our path $ g(x, y) = k$ is nothing but a level curve of the function $ z = g(x, y)$. (Note that this is a *different* function from the one that describes the height of Mount Glass!)

For the sake of intuition, let's make some assumptions: let's say that $ g(x, y) = k$ is a simple closed curve which we're traversing clockwise, and that $ \nabla g$ always points in (that is, to your right as you walk around the path).

Okay, off we go on our hike. Hold your right arm straight out from your body. If you look at the shadow of your arm, you can see that it's perpendicular to the path painted on the floor. Thus, per our assumptions, this is $ \nabla g$.

Pretend you're on an uphill portion of the path. Here, you can increase your elevation by just moving forward. This means that "straight up the hill" is going to be a little bit forward -- in particular, your arm isn't pointing exactly that way.

Now pretend you're on a downhill portion of the path. Here, you can increase your elevation by walking backward. Again, this means your arm isn't pointing "straight up the hill" -- that would be a little bit behind you.

Compare this to the situation where you're at a high spot on the path. You can't get higher by going forward \*or\* backward. If you wanted to get higher, you'd have to step off the path, and you're not allowed to do that -- "straight up the hill" is in precisely the wrong direction for you to do anything with it. Now look at your arm -- it \*is\* pointing straight up the hill. (Or maybe straight down. Same deal.)

Now let's bring this home by putting some math on it. "Straight up the hill" is precisely $ \nabla f$; again, your arm is pointing in the direction of $ \nabla g$. At a high spot, your arm and "straight up the hill" are in the same direction. That is, $ \nabla f$ and $ \nabla g$ are *parallel.* A great way to think about when two vectors are parallel is that one of them has to be a scalar multiple of the other -- in other words, $ \nabla f = \lambda\cdot\nabla g$.

Yay!
