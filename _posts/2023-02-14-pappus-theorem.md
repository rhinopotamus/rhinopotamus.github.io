---
layout: post
title:  "Pappus's theorem"
tags: math calculus 
katex: True
---

(This post will update several times, as I use it as a scratchpad.)

In my Calculus II class, we were talking about solids of revolution, and how calculus allows us to pretty easily solve a suite of problems that the Greek philosopher-mathematicians spent a lot of time thinking about (mostly because it was economically useful to have accurate computations of the volumes of pithoi and amphorae, both of which are solids of revolution). I mentioned something about how Archimedes had solved a special case (the volume of a paraboloid), and that there was some other guy who did something cool in this regard, but I couldn't pull the name immediately.

The other guy is Pappus of Alexandria, and in modern language, Pappus's theorem[^1] goes like this: Say you have a plane figure $F$ which you are revolving around an external axis. The volume $V$ of the solid thus swept out is equal to the product of the area $A$ of $F$ and the distance $d$ traveled by the centroid of $F$: 

$$V = A\cdot d.$$

In historical context this is maybe one of the crowning achievements of any Greek geometer not named Euclid. With the tools of calculus, this becomes a pretty straightforward problem that you could reasonably give to an undergraduate. In particular:

## There's a special case that's easy

Say that your setup is like this:

![A sketch of the region described in the paragraph below](/images/pappus-1.png)

 To describe this in words, $F$ is bounded by two functions $f$ and $g$, where $f$ is the upper edge and $g$ is the lower edge. These functions intersect at $x=a$ and $x=b$, and we're rotating around the axis $x=c$ (for "center"), where $a < b < c$.

The method of shells gives you a straightforward way to calculate the volume of the solid of revolution: Draw a vertical slice of this region and revolve it around the axis $x=c$. What you get is something like the skin of a tin can. The height of that slice is $f(x) -g(x)$, the thickness is $\Delta x$, and the circumference is $2\pi r$, where $r$ is the (horizontal) distance between the slice location and the center of revolution $c$. Looking at this picture will show you that $r = c-x$:

![A sketch of a vertical slice revolved around x=c](/images/pappus-2.png)

(My art is very beuatiful and very accurate. This is a math blog, not a drawing blog.)

Imagine cutting this big tin can open and unrolling it so it lies flat. You therefore have a rectangular slab, whose volume is length times width times height: $[f(x)-g(x)][2\pi(c-x)]\Delta x$. Therefore, the volume is:

$$V = \int_{x=a}^b 2\pi [f(x)-g(x)][c-x]\ dx.$$

[^1]: I should be slightly more careful and call this Pappus's *centroid* theorem, because there's [another pretty famous theorem due to Pappus](https://en.wikipedia.org/wiki/Pappus%27s_hexagon_theorem) that comes up in geometry.