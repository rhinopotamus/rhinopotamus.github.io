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

The stuff after the "if" I usually call the "hypotheses;" the stuff after the "then" I usually call the "conclusion." The theorem is *the whole sentence*: the promise that if the hypotheses are met, the conclusion results.

A lot of people learning theorems for the first time think that the theorem is *just* the conclusion. For instance, if you asked them what the extreme value theorem is, many a calculus student would reply, "there exist input values $c$ and $d$ in $[a,b]$ such that $f(c) \leq f(x) \leq f(d)$ for all other input values $x$ in $[a,b]$." This is not true! The hypotheses -- and there are three in this case -- are all *necessary* to reach the conclusion.

I chose this theorem because there are some easy examples illustrating *why* the hypotheses are necessary:

1. The first hypothesis is that $f$ is continuous. If we throw that hypothesis away, bad things can happen. Consider $f(x) = \frac{1}{x^2}$ on the interval [-1, 1]. This function isn't bounded above, so it definitely doesn't attain a maximum.
2. The second hypothesis is that the interval is closed. Let's think about the function $f(x) = x^2$ on the interval $(0 ,1)$. If the function *was* going to attain its min and its max, they would be at $x=0$ and $x=1$ respectively, so if we throw those inputs away from our interval, we're going to run into problems.
3. The third hypothesis is that the interval is bounded. Consider the function $f(x) = \frac{1}{1+x^2}$; this is a perfectly nice function that's continuous everywhere. But if we look at the interval $[0, \infty]$, we have an asymptote problem: because $f$ keeps on decreasing, it never hits a minimum.

An illustration would be nice here.

## The Pythagorean theorem as an implication

> Label the sides of a triangle $a$, $b$, and $c$. If the triangle is right (and $c$ is the hypotenuse), then $a^2 + b^2 = c^2$.

## Biconditionals

> If $a$, $b$, and $c$ are the side lengths of a triangle, and $a^2 + b^2 = c^2$, then the triangle is right.