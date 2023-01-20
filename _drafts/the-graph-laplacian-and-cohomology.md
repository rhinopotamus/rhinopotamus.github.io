---
layout: post
title:  "The graph Laplacian and cohomology"
tags: math graphs 
excerpt: True
katex: True
---

I'm leading a directed study with a student about spectral graph theory this semester. (Long story short, he was in my linear algebra class, another student saw a cool thing about clustering using eigenvalues of the graph Laplacian in [Tim Chartier's book][tc-book], and the three of us did some summer research work about it.) This means that I am learning a lot of stuff about graph theory and linear algebra, and this often bleeds out into other weird branches of mathematics. Here's a good example.

Suppose that $$G$$ is a graph with vertex set $$V(G)$$ and edge set $$E(G)$$. Build the degree matrix $$D$$ (a diagonal matrix indexed by the vertices whose diagonal entries are given by the degree of each vertex) and the adjacency matrix $$A$$ (a matrix indexed by the vertices such that $$A(v,u) = 1$$ if $$v$$ is adjacent to $$u$$ and $$0$$ otherwise). The *graph Laplacian* is the matrix $$L = D - A$$. 

Pick some function $$f:V(G) \to \Reals$$. It's useful to think of $$f$$ as a column vector in $$\Reals^{\vert V \vert}$$. The *Rayleigh quotient* of $$f$$ with respect to the Laplacian is defined as:

\begin{equation} 
\frac{\langle f, Lf \rangle}{\langle f, f \rangle}
\end{equation}

[The notes we were looking at][fan-chung-ch1] assert the following:[^1]

\begin{equation} 
\frac{\langle f, Lf \rangle}{\langle f, f \rangle} = \frac{\displaystyle\sum_{(u, v) \in E}(f(u)-f(v))^2}{\displaystyle\sum_v f(v)^2 d_v}
\end{equation}

We wanted to better understand this calculation, because the Rayleigh quotient is important for picking out eigenvalues of $$L$$. The denominator ends up being straightforward, but in the numerator, I dragged us lengthwise through the following honestly horrific calculation, which you should not look very hard at other than to note that it involves double sums, index gymnastics, and every other bad thing.




[tc-book]: https://www.amazon.com/When-Linear-Anneli-Mathematical-Library/dp/0883856492
[fan-chung-ch1]: https://mathweb.ucsd.edu/~fan/research/cb/ch1.pdf
[^1]: NB that things are set up a little differently there, using the normalized Laplacian, but this Rayleigh quotient calculation works out the same way.