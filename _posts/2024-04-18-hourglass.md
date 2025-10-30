---
layout: post
title:  "What shape is an hourglass?"
tags: math calculus
image: https://rhinopotamus.github.io/images/hourglass.jpg
katex: True
---

If I ask you what shape an hourglass is, there is a very specific shape that leaps to mind. (Maybe there is also theme music.) 

![Days of Our Lives title card](/images/hourglass.jpg)

For Physics Reasons (TM), fluids[^1] will flow more quickly out of a more full container than they will out of an emptier container, so if we want the level of the fluid to drop consistently, we need the sides to taper in to compensate. 

Exactly how much taper do we need? What shape, in fact, is an hourglass? Turns out this is a fun question to explore with just a little calculus.

## Solids of revolution

A reasonable assumption to make, that puts this problem neatly in the realm of a Calculus II course, is that the hourglass is a solid of revolution. Let's say that the radius of the tank is a function of the height, let's say $r(y)$; we probably want to set the pinch-point of the hourglass at $y=0$. 

We can write down an integral with respect to $y$ that gives you the volume of sand remaining in the top bulb. Maybe we should set this up as a function of the current level of sand, $V(h)$. Probably you can do this using good choices for your bounds of integration. $y=0$ is certainly your bottom bound, but what's your top bound?

$V$, the remaining volume of sand in the top bulb of the hourglass, is really a function of time -- it's really $V(t)$. Let's see what we can learn about $\dfrac{dV}{dt}$.

There are two approaches to this next point: one of them uses the Second[^2] Fundamental Theorem of Calculus, and the other uses the slice-approximate-integrate paradigm that you probably are thinking about in order to write down that integral in the first place.

### Second FTC approach

The way that $V$ depends on $t$ is sneaky. One of your bounds of integration -- the one that's the current level of sand -- is *also* a function of time. I don't know exactly what function it is, but also I don't care; I could just write it as, for instance, $h(t)$, and then use the Second FTC to find out something interesting about $\dfrac{dV}{dt}$ in relation to $\dfrac{dh}{dt}$.

### Slice-approximate-integrate approach

A nice way to think about how to write down that integral for $V$ is to write down a wrong-but-good approximation for the volume of a little slice $\Delta V$, then add up all the slices: $V \approx \sum \Delta V$. If we play our cards right, this is a Riemann sum, so we can shove it through a limit process to turn it into an integral that produces the exact value.

What's nice about this is that since $\dfrac{dV}{dt} \approx \dfrac{\Delta V}{\Delta t}$, we can just divide whatever we come up with for $\Delta V$ by $\Delta t$ to come up with a decent approximation for the derivative. 

In particular, $\Delta V$ will probably involve a small thickness, which I will refer to as a $\Delta h$. Dividing both sides by $\Delta t$ will thus produce both a $\dfrac{\Delta V}{\Delta t}$ and a $\dfrac{\Delta h}{\Delta t}$. We can thus find out something interesting about $\dfrac{dV}{dt}$ in relation to $\dfrac{dh}{dt}$.

## Physics time

Whichever approach we have taken, we now have an equation relating $\dfrac{dV}{dt}$ to $\dfrac{dh}{dt}$. Neat!

For Physics Reasons (TM), the rate of change of the volume of the water is proportional to the square root of the water level. I'll take a brief detour here to say what those physics reasons are, but if you're willing to take it on faith, you can skip ahead.

If you poke a hole in the bottom of a water tank, the volume you lose is a li'l tube of water coming out of the spout hole. So, $\Delta V = $(area of spout hole)$\cdot v\cdot \Delta t$, where little-v is now the velocity at which the water is leaving the hole.

What's $v$? The kinetic energy you gain by the water moving is the same as the potential energy you lose by the water level dropping a bit, so $\frac12 mv^2 = mgh$. Conclude that $v = \sqrt{2gh}$.

Blob some stuff together into a constant of proportionality and you have what you want.

## Differential equations 

The physics sentence we just said, "the rate of change of the volume of the water is proportional to the square root of the water level," is in fact a differential equation. That is, it's a statement about $\dfrac{dV}{dt}$; write it down.

Now you know two things about $\dfrac{dV}{dt}$, so they must be equal. If you equate these two things, you suddenly have an interesting differential equation about $h$!

You could make lots of interesting observations about $h$ based on this differential equation. But in particular:

## We're trying to design an hourglass

If you are designing an hourglass, you probably want the sand level to fall at a uniform rate. What does that tell you about $\dfrac{dh}{dt}$?

Conclude that $r$ is proportional to $h^{1/4}$.

---

[^1]: Technically the sands of an hourglass are not quiiite a fluid (and neither are the days of our lives), but this is a good enough approximation for most purposes. A similar device that uses actual water instead of sand is called a clespydra.

[^2]: Fight me.