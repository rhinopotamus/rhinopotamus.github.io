---
layout: post
title:  "Integrating something two ways"
tags: math calculus 
katex: True
---

Today in Calculus II we were playing with the [Wolfram Problem Generator][wpg], which gave us the following *very* tricky integral:

$$
\int t^2 \arcsin t \ dt
$$

Clearly this is an integration by parts problem, but which way do you pick $u$ and $dv$? Either way you do it, you end up needing a trick.

## Way 1: $u = \arcsin t$, $dv = t^2\ dt$

This seems like the obvious way if you are listening to the "LIATE" mnemonic, which tells us that inverse trigonometric functions are good choices for $u$, since taking their derivative turns them into something algebraic:

$$ 
\begin{array}{ll}
u=\arcsin t                     & v = \frac13 t^3 \\
du = \dfrac{1}{\sqrt{1-t^2}}\ dt & dv = t^2 \ dt  
\end{array}
$$

Here's your second integral, which is at least algebraic:

$$\int \frac13 t^3\ \frac{1}{\sqrt{1-t^2}}\ dt $$

But what to do with this one? Since I see a burrito -- er, a composite function, I think substituting $u=1-t^2$ is a good choice, but then $du = -2t\ dt$ won't entirely kill that $t^3$.

Here's the trick: Note that if $u = 1-t^2$, then $t^2 = 1-u$, so $t^3 = t(1-u)$. Then everything works out nicely:

$$
\begin{align*}
\int \frac13 t^3\ \frac{1}{\sqrt{1-t^2}}\ dt 
&= \frac13\int t\ (1-u)\ \frac{1}{\sqrt{u}} \ \frac{du}{-2t}.
\end{align*}
$$

Fill in the details from here; it's a good time. Don't forget to assemble the whole integration by parts business.

## Way 2: $u = t^3$,  $dv = \arcsin t\ dt$

There are actually two tricks this time. The first trick is only somewhat tricky, and it's to integrate $dv$ through a clever use of integration by parts. (It's similar to how we figure out $\int\ln t\ dt$, if you know that trick.) We're going to pick $u = \arcsin(t)$ and $dv = 1\ dt$:

$$ 
\begin{array}{ll}
u=\arcsin t                     & v = t \\
du = \dfrac{1}{\sqrt{1-t^2}}\ dt & dv = 1 \ dt  
\end{array}
$$

$$
\begin{align*}
\int\arcsin t\ dt &= t \arcsin t - \int \frac{t}{\sqrt{1-t^2}}\ dt \\
&= t \arcsin t - \int \frac{1}{\sqrt{u}}\ \frac{du}{-2} \\
&= t\arcsin t + \frac12 \int u^{-1/2} \ du \\
&= t \arcsin t + \sqrt{1-t^2}
\end{align*}
$$

That was fun. Now we can write down $v$ and proceed with the original integration by parts:

$$ 
\begin{array}{ll}
u=t^2 & v = t \arcsin t + \sqrt{1-t^2} \\
du = 2t\ dt & dv = \arcsin t \ dt  
\end{array}
$$

$$
\begin{align*}
\int t^2\arcsin t \ dt &= t^3 \arcsin t + t^2\sqrt{1-t^2} - \int 2t(t \arcsin t + \sqrt{1-t^2})\ dt \\
&= t^3 \arcsin t + t^2\sqrt{1-t^2} - 2\int t^2 \arcsin t \ dt + \int -2t\sqrt{1-t^2}\ dt
\end{align*}
$$

Here comes the second trick: What we're interested in is $\int  t^2 \arcsin t\ dt$, which we can treat as an unknown. I've got 1 of 'em on the LHS, and -2 of 'em on the RHS. Why don't we just add the ones on the RHS over to the LHS?

$$
3 \int t^2\arcsin t \ dt = t^3 \arcsin t + t^2\sqrt{1-t^2} + \int -2t\sqrt{1-t^2}\ dt 
$$

I'll let you take it from there.

## Lastly, some algebra

The astute reader will notice that the two results are slightly different. Do some algebra to convince yourself that they're actually equivalent. (Sometimes when this happens, you need the two constants of integration to be different; graph them in Desmos or your favorite plotting software to see if you think this is the case this time.)

[wpg]: https://www.wolframalpha.com/problem-generator/