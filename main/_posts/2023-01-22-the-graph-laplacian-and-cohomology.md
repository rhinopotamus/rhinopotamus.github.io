---
layout: post
title:  "The graph Laplacian and cohomology"
tags: math graphs 
katex: True
---

I'm leading a directed study with a student about spectral graph theory this semester. (Long story short, he was in my linear algebra class, another student saw a cool thing about clustering using eigenvalues of the graph Laplacian in [Tim Chartier's book][tc-book], and the three of us did some summer research work about it.) This means that I am learning a lot of stuff about graph theory and linear algebra, and this often bleeds out into other weird branches of mathematics. Here's a good example, the moral of which is that if something is hard or annoying, you may be looking at it wrong.

Suppose that $G$ is a graph with vertex set $V(G)$ and edge set $E(G)$. Build the degree matrix $D$ (a diagonal matrix indexed by the vertices whose diagonal entries are given by the degree of each vertex) and the adjacency matrix $A$ (a matrix indexed by the vertices such that $A(v,u) = 1$ if $v$ is adjacent to $u$ and $0$ otherwise). The *graph Laplacian* is the matrix $L = D - A$. 

Pick some function $f:V(G) \to \Reals$. It's useful to think of $f$ as a column vector in $\Reals^{\vert V \vert}$. The *Rayleigh quotient* of $f$ with respect to the Laplacian is defined as:

$$
\frac{\langle f, Lf \rangle}{\langle f, f \rangle}
$$

[The notes we were looking at][fan-chung-ch1] assert the following:[^1]

$$ 
\frac{\langle f, Lf \rangle}{\langle f, f \rangle} = \frac{\displaystyle\sum_{(u, v) \in E}(f(u)-f(v))^2}{\displaystyle\sum_v f(v)^2 d_v}
$$

We wanted to better understand this calculation, because the Rayleigh quotient is important for picking out eigenvalues of $L$. The denominator ends up being straightforward, but in the numerator, I dragged us lengthwise through the following honestly horrific calculation, which you should not look very hard at other than to note that it involves double sums, index gymnastics, overly-clever relabeling, and every other bad thing.

$$
\begin{align*}
    \langle f, Lf \rangle &= \sum_u f(u) (Lf(u)) = \sum_u f(u) \left[\sum_v L(u, v) f(v)\right] \\
    & = \sum_u \sum_v f(u) (D(u,v) - A(u,v)) f(v) \\
    &= \sum_u \left[ d_u f(u)^2 - \sum_{v \text{ adj. } u}f(u) f(v) \right]
    = \frac12 \left( \sum_u \left[ 2 d_u f(u)^2 - \sum_{v \text{ adj. } u}2 f(u) f(v) \right] \right) \\
    &= \frac12 \left( \sum_u  d_u f(u)^2 + \sum_u  d_u f(u)^2 - \sum_u\sum_{v \text{ adj. } u}2 f(u) f(v) \right) \\
    &= \frac12 \left( \sum_u  d_u f(u)^2 + \sum_v  d_v f(v)^2 - \sum_u\sum_{v \text{ adj. } u}2 f(u) f(v) \right) \\
    &= \frac12 \left( \sum_u \left[\sum_{v\text{ adj. } u} 1\right] f(u)^2 + \sum_v  \left[\sum_{u\text{ adj. } v} 1\right] f(v)^2 - \sum_u\sum_{v \text{ adj. } u}2 f(u) f(v) \right) \\
    &= \frac12 \sum_u \sum_{v\text{ adj. }u} f(u)^2 + \frac12 \sum_v \sum_{u\text{ adj. }u} f(v)^2 - 
    \frac12 \sum_u\sum_{v \text{ adj. }u} 2f(u) f(v) \\
    &= \sum_{(u, v) \in E} f(u)^2 + \sum_{(u, v) \in E} f(v)^2 - \sum_{(u, v) \in E} 2f(u) f(v)  \\
    &= \sum_{(u, v) \in E} \left[f(u)^2 + f(v)^2 - 2 f(u) f(v) \right] = \sum_{(u, v) \in E}(f(u) - f(v))^2
\end{align*}
$$

Any time a calculation turns out this terrible and requires this many weird tricks, that's a good sign that the approach you have chosen is somehow, morally, the wrong choice. [So I went fishing on math twitter.][tweet]

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">OKAY SO let&#39;s say L is the Laplacian matrix of a graph G, and f is some function from V(G) to R. It&#39;s true that &lt;f, Lf&gt; = sum (f(u)² - f(v)²), where the sum is over all the pairs of adjacent vertices u and v. Is there a *good* way to see this?</p>&mdash; Dr Spencer Bagley 🏳️‍🌈 (@sbagley) <a href="https://twitter.com/sbagley/status/1615462883571421186?ref_src=twsrc%5Etfw">January 17, 2023</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

(Please ignore the typos, lol.)

The consensus of a couple of my smart twitter pals was that you have better luck if you think of $L$ not as $D-A$ -- which was, ultimately, the choice that led to every other bad thing in that calculation above -- but instead as $B B^T$. But who is this mysterious $B$, you ask? Good question.

$B$ is the *incidence matrix*. The rows of $B$ are indexed by the vertices of $G$, and the columns of $B$ are indexed by the edges of $G$. Put some kind of orientation on all the edges; I don't care what it is. Then:

$$
B(v, e) = 
\begin{cases}
1 & e \text{ starts at } v \\
-1 & e \text{ ends at } v \\
0 & \text{otherwise}
\end{cases}
$$

(Note, btw, that I don't care if you choose the opposite sign convention for $B$; everything still works out the same.)

You should spend one to four minutes convincing yourself that $B B^T = D - A$; just kinda imagine what happens on each row. Once you've done that, you can think about $B$ itself. If you know what homology is (which, uh, maybe I do sometimes?), you may be thinking to yourself, huh, $B$ is some kind of linear map $B:E(G) \to V(G)$ to where $B(e) = u -v$, gee whiz, that sounds like the boundary operator. You're right! What's more, $B^T$ is therefore the coboundary operator. After all, a graph is nothing more than the 1-skeleton of a simplicial complex, so we may as well do homology stuff to it.

One more kinda complication here is that we started with a function $f:V(G) \to \Reals$ -- that is, a vertex form -- which we wanted to think about as $f\in\Reals^V$. Maybe we actually want to do some de Rham cohomology, then. That's fine; $B^T$ is still the coboundary operator. Specifically, $B^Tf(u, v) = f(u) - f(v)$. You can think of $B^T:\Reals^V\to\Reals^E$ or you can think of $B^T:\Omega^0(G) \to \Omega^1(G)$, whichever you like more.

Here is the punchline of this blog post. With this setup, the Rayleigh quotient calculation becomes a one-liner:

$$
\langle f, Lf \rangle 
= \langle f, B B^T f \rangle 
= \langle B^T f, B^T f \rangle = \sum_{(u, v) \in E} (B^T f(u,v))^2 = \sum_{(u, v) \in E} (f(u) - f(v))^2.
$$

And if you don't think that kicks ass, then you can get the hell out of my face.

---

[tc-book]: https://www.amazon.com/When-Linear-Anneli-Mathematical-Library/dp/0883856492
[fan-chung-ch1]: https://mathweb.ucsd.edu/~fan/research/cb/ch1.pdf
[^1]: NB that things are set up a little differently there, using the normalized Laplacian, but this Rayleigh quotient calculation works out the same way.
[tweet]: https://twitter.com/sbagley/status/1615462883571421186