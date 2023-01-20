---
layout: post
title:  "katex testing"
date:   2023-01-20 12:24 -0700
katex: True
---
Environments with no backslashes seem to work fine:

\begin{equation} 1 + 3 = 4 \end{equation}

What about double backslashes inside double dollar signs? Yep, that works:

$$ \begin{matrix} 1 & 2 \\ 3 & 4 \end{matrix} $$

What about align* inside math mode?

$$ \begin{align*} 1 &= 2 \\ 3 &= 4 \end{align*} $$

something more complicated:

$$ \begin{CD}
   A @>a>> B \\
@VbVV @AAcA \\
   C @= D
\end{CD} $$

Okay so what solves a lot of the problem is to just put things inside math mode to begin with instead of hoping that katex autoparses correctly after markdown is done with it.

Now I'm going to push this to web to make sure this still works remotely and not just locally.
