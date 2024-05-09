---
layout: post
title:  "Approximating π"
tags: math calculus
image: https://rhinopotamus.github.io/images/tfd-pi.gif
katex: True
---

A fun thing to do at the end of a Calculus II class is to use Taylor series to compute values of various functions. For instance, I have a whole problem set about the "68-95-99.7" rule, where we find a Taylor series for the normal distribution and then integrate it. Here's another fun application:

## Approximating π

"Everybody" knows that $\pi \approx 3.14$. Some people know considerably more digits off the top of their head. ([You should probably be suspicious of those people.](https://www.toothpastefordinner.com/index.php?date=031208)) 

![Toothpaste for Dinner comic](/images/tfd-pi.gif)

But how do we actually know what those digits are? When you ask your computer or calculator what π is, how does it know? There are lots of approaches to this question (some more efficient than others) but here's one that's fun and accessible to students in a Calculus 2 course.

When I start thinking about π, I start thinking about radians. For instance, I know that $\tan\left(\frac\pi4\right)= 1$. Therefore, $\pi = 4\arctan(1)$. This gives me an idea: I happen to have recently completed the following exercise in Taylor series manipulation that tells me the Taylor series for the arctangent function.

### Cheap ways to find Taylor series

Finding Taylor series can be a real pain in the ass. You have to take all these derivatives, and sometimes they just get worse and worse. For instance, try taking a few derivatives of $f(x) = \arctan(x)$:

$$
\begin{align*}
f(x) &= \arctan(x) \\
f'(x) &= \dfrac{1}{1+x^2} = (1+x^2)^{-1}\\ 
f''(x) &= (-1)(1+x^2)^{-2}\cdot 2x = -2x (1+x^2)^{-2} \\
f'''(x) &= (-2)(1+x^2)^{-2} + (-2x)(-2(1+x^2)^{-3}(2x)) \\
&= -2(1+x^2)^{-2} +8x^2(1+x^2)^{-3} \\
f^{(4)}(x) &= \ldots
\end{align*}
$$

These are just going to keep getting worse and worse because of the chain rule / product rule interaction. Things will simplify a bit when I start plugging in zero, but I do have to keep all of these terms in order to find the next derivative.

This is the part in the infomercial where it's all black and white and someone is just flinging an entire bowl of popcorn across the room. There has to be a better way!

![infomerical gif of man drinking goofily from sink](/images/better-way.gif)

Well, I'm noticing that $f'(x)$ is shaped like $\dfrac{1}{1-u}$, whose Taylor series I know to be $1 + u + u^2 + \ldots = \displaystyle\sum_{k=0}^\infty u^k$. Turns out I can just substitute:

$$
\begin{align*}
\dfrac{1}{1+x^2} = \dfrac{1}{1-(-x^2)} &= 1 + (-x^2) + (-x^2)^2 + ... = \displaystyle\sum_{k=0}^\infty (-x^2)^k \\
&= 1 - x^2 + x^4 - x^6 + \ldots = \displaystyle\sum_{k=0}^\infty (-1)^k x^{2k}
\end{align*}
$$

And then I can just integrate:

$$
\begin{align*}
\arctan(x) = \int\dfrac{dx}{1+x^2} &= \int (1 - x^2 + x^4 - x^6 + \ldots)\\
&= C + x - \dfrac{x^3}{3} + \dfrac{x^5}{5} - \dfrac{x^7}{7} + \ldots \\
&= C + \displaystyle\sum_{k=0}^\infty (-1)^k \dfrac{x^{2k+1}}{2k+1}
\end{align*}
$$

We should probably figure out the value of our constant of integration. Conveniently I know that $\tan(0) = 0$ so $\arctan(0) = 0$. Therefore $C = 0$, how nice. 

I therefore have the following nice result:

$$
\arctan(x) = \displaystyle\sum_{k=0}^\infty (-1)^k \dfrac{x^{2k+1}}{2k+1}.
$$

### Convergence behavior 

I should probably be a little bit careful about where this series representation converges. In particular, since I started with the geometric series $\displaystyle \sum u^k = \dfrac{1}{1-u}$, which only converges on the interval $-1<u<1$, my series representation for $\dfrac{1}{1+x^2}$ can only converge on $-1<x^2 < 1$ -- that is, on $-1< x < 1$. It's a theorem that integrating term-by-term doesn't change the radius of convergence, so that means that my representation for $\arctan(x)$ can only converge on this same interval.

This may be trouble, because we were interested in the fact that $\pi = 4\arctan(1)$. If my series doesn't converge at $x=1$, I'm shit out of luck at the beginning of the exercise. Fortunately for us, weird things sometimes happen at the endpoints of intervals of convergence when you start manipulating them -- integrating term-by-term doesn't change the *radius* of convergence, but it may change the *interval* of convergence.

This is a particularly good example of this weird phenomenon. The series representation $\dfrac{1}{1+x^2} = 1 - x^2 + x^4 + \ldots$ does not converge at $x=1$. However, the series representation $\arctan(x) = x - \dfrac{x^3}{3} + \dfrac{x^5}{5} - \dfrac{x^7}{7} + \ldots$ *does* converge at $x=1$:

$$
\arctan(1) = \displaystyle\sum_{k=0}^\infty (-1)^k \dfrac{1^{2k+1}}{2k+1} = \displaystyle\sum_{k=0}^\infty (-1)^k \dfrac{1}{2k+1}.
$$

This is an alternating series whose *k*th term goes to zero, so it converges!

(Aside: It's interesting to check that this representation also converges at $x=-1$, so the interval of convergence is now $-1 \leq x \leq 1$.)

### We're in business!

Let us therefore calculate π:

$$
\pi = 4\arctan(1) = 4 \cdot \displaystyle\sum_{k=0}^\infty \dfrac{(-1)^k}{2k+1} \\
= 4\left(1 - \dfrac13 + \dfrac15 -\dfrac17 + \dfrac19 - \ldots \right)
$$

Truncating this infinite sum (that is, computing $\displaystyle\sum_{k=0}^n (\ldots)$) gives us a sequence of ever-closer representations of π. I recommend typing some stuff into a spreadsheet and playing around a bit, but here's the first eleven approximations:

| n   | 0 | 1      | 2      | 3      | 4      | 5      | 6      | 7      | 8      | 9      | 10     |
|-----|---|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
| π ≈ | 4 | 2.6667 | 3.4667 | 2.8952 | 3.3397 | 2.9760 | 3.2837 | 3.0171 | 3.2524 | 3.0418 | 3.2323 |

You may notice that these are, uhhh, bad. Let's figure out how bad exactly.

### The alternating series error bound

A fun fact about convergent alternating series $S = \displaystyle\sum_{k=0}^\infty (-1)^k a_k$ is that each pair of subsequent entries in the sequence of partial sums consists of an underestimate and an overestimate. This means that the size of the error you get when you approximate the infinite series $S$ by the *n*th partial sum $S_n = \displaystyle\sum_{k=0}^n (-1)^k a_k$ is bounded by the size of the next term:

$$|S - S_n| < a_{n+1}$$

(In practice, the error is a bit more than half as much. Do you see why?)

In our case, we get that

$$|\pi - S_n| < \dfrac{4}{2n+3}$$

Suppose we wanted to know how far out we have to go in order to get the first two decimal places right -- that is, to confidently write $\pi \approx 3.14$. It would suffice to have our error below 0.005 (think about how rounding works):

$$
\begin{align*}
\dfrac{4}{2n+3} &< 0.005  \\
\dfrac{4}{0.005} &< 2n + 3 \\
800 &< 2n + 3 \\
n &> \dfrac{797}2 = 398.5
\end{align*}
$$

Therefore, we have to have $n=399$, and remember that we started counting at zero -- we have to add up *four hundred* of these damn things in order to even be sure that our first two decimal places are right!![^1]

I guess we're still stuck in black-and-white infomercial territory:

![a woman struggling heroically to wrap up leftovers with plastic wrap](/images/saran-wrap.gif)

### Why is this *so bad*?

Before we try anything else, we should understand the problem:

![Ms. Frizzle saying "if at first you don't succeed, find out why"](/images/frizzle.png)

I wasn't just talking about convergence behavior above for reasons of nitpickery (although I am not immune to such impulses). This is actually the precise reason why this series converges so slowly. Remember that our interval of convergence was $-1 \leq x \leq 1$, and we are in fact dealing with $x=1$. Therefore, we are as far away from the center of convergence as it is possible to be and still converge. From this lens, *of course* we're converging super slow: we have some sense that the goodness of an approximation is controlled both by the degree of the approximation and by the distance away from the center.

This also gives me an idea for how to improve this process for approximating π: maybe there's a better point, further inside the interval of convergence, where we'll get faster convergence behavior. [Hmm...]({% 2024-05-09-approximating-pi-pt-2 %})

[^1]: Remember that in practice our error is usually a bit more than half as much as the error bound predicts. If you look at a spreadsheet you'll see that indeed our approximation to π starts consistently rounding to 3.14 around n = 293. 