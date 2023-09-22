---
layout: post
title:  "The Pythagorean theorem"
tags: math theorems 
katex: True
---

What's the Pythagorean theorem?

If you're like most people, your immediate answer is:

$$
a^2 + b^2 = c^2
$$

If you're like most people, you may be surprised if I tell you that this is only half the story. The problem is that the Pythagorean theorem is, in fact, *a theorem*, which means something additional and specific. But what?

## What is a theorem, anyway?

(I feel like I could write an entire blog post with just that title.) 

I could tell you at the outset that a theorem is a justified implication, and let those two big words do all the heavy lifting, but that's unsatisfying. Instead, I'll say that *a theorem is a promise*: it's a guarantee that if certain conditions are met, certain outcomes must result. 

To illustrate what I'm saying here, let's look at a different example, but one that's still fairly familiar: the *extreme value theorem* in the context of first-semester calculus. Here's what this theorem says:

> If $f$ is a continuous function on the closed, bounded interval $[a,b]$, then $f$ must attain a minimum and a maximum -- that is, there exist input values $c$ and $d$ in $[a,b]$ such that $f(c) \leq f(x) \leq f(d)$ for all other input values $x$ in $[a,b]$.

Zoom out from the details for a second and look at the structure:

> If \_\_\_, then \_\_\_.

The stuff after the "if" I usually call the "hypotheses;" the stuff after the "then" I usually call the "conclusion." The theorem is *the whole sentence*: the promise that *if* the hypotheses are met, *then* the conclusion results.

A lot of people learning theorems for the first time think that the theorem is *just* the conclusion. For instance, if you asked them what the extreme value theorem is, many a calculus student would reply, "there exist input values $c$ and $d$ in $[a,b]$ such that $f(c) \leq f(x) \leq f(d)$ for all other input values $x$ in $[a,b]$." This is not true! The hypotheses -- and there are three in this case -- are all *necessary* to reach the conclusion.

I chose this theorem because there are some easy examples illustrating *why* the hypotheses are necessary:

1. The first hypothesis is that $f$ is continuous. If we throw that hypothesis away, bad things can happen. Consider the piecewise function I've drawn below, which is defined everywhere on the interval $[0,2]$ but is *discontinuous* on this interval[^1]. This function doesn't attain a maximum on this interval because of the way it jumps.
2. The second hypothesis is that the interval is closed. Let's think about the function $f(x) = x^2$ on the *open* interval $(0 ,1)$. If the function *was* going to attain its min and its max, they would be at $x=0$ and $x=1$ respectively, so if we throw those inputs away from our interval, we're going to run into problems.
3. The third hypothesis is that the interval is bounded. Consider the function $f(x) = \frac{1}{1+x^2}$; this is a perfectly nice function that's continuous everywhere. But if we look at the unbounded interval $[0, \infty)$, we have an asymptote problem: because $f$ keeps on decreasing, it never hits a minimum.

![A function on the interval [0, 2] with a jump discontinuity](/images/discontinuous.png)
![The function f(x) = x^2 on the open interval (0, 2)](/images/open-interval.png)
![The function f(x) = 1/(1+x^2)](/images/unbounded-interval.png)

So you can see that each of the hypotheses is necessary. Why it is that they justify my promise is a harder question; this is the job of a proof, and a proof of this theorem is a little outside the scope of this blog post.[^2]

## The Pythagorean theorem as an implication

Let's now return to the Pythagorean theorem, which is indeed a theorem, and thus must have the same if-then structure that all theorems have. The sneaky hypothesis that is hiding somewhere in everyone's mental image but doesn't come out verbally is that the triangle is a *right* triangle:

> Suppose the sides of a triangle have lengths $a$, $b$, and $c$. *If* the triangle is right (and $c$ is the hypotenuse), *then* $a^2 + b^2 = c^2$.

And you can tell that this hypothesis is also necessary. For instance, consider an equilateral triangle where each side length is 1 -- so $a = b = c = 1$, no matter which way you label. Such a triangle is certainly a legit triangle. But then $a^2 + b^2 = 1^2 + 1^2 = 2$, which is certainly not the same as $c^2 = 1$.

## Biconditionals

Sometimes we get even nicer theorems that are actually two promises rolled into one; we call such things *biconditional*. The Pythagorean theorem is actually such a theorem. Here's the other promise:

> Suppose the sides of a triangle have lengths $a$, $b$, and $c$. If $a^2 + b^2 = c^2$, then the triangle is right.

You'll notice that the only difference between this promise and the last one is that the roles of the hypothesis and the conclusion are switched. I think that helps explain why we call this a "biconditional" -- it's a "conditional" promise that goes both ways.

The fact that the Pythagorean theorem has this other facet, that it goes both ways, is actually really cool, and it leads to the thing I was thinking about that originally made me write this blog post. This is a very simple device that you can use to be sure that you have a right angle:

Image goes here.

How would you use such a device to accomplish this task? If you want to think more about it before I spoil it, don't scroll further. 

Here are three hints in increasing order of hintiness:

1. Consider that there are 13 evenly-spaced knots in this rope.
2. Consider that these 13 knots mark out 12 equal lengths of rope.
3. Consider that $3 + 4 + 5 = 12$.

You may recognize $(3, 4, 5)$ as a *Pythagorean triple* -- that is, that $3^2 + 4^2 = 5^2$. (Check!) Therefore, a triangle that has one side of length 3, a second side of length 4, and a third side of length 5 meets the hypothesis of the second promise of the Pythagorean theorem -- and, therefore, *must be a right triangle*.

Second image goes here.

[^1]: I thought about writing this with the example function $f(x) = \frac{1}{x^2}$, but the annoying thing about that function is that technically, it is continuous on its entire domain.
[^2]: It's fun, though.