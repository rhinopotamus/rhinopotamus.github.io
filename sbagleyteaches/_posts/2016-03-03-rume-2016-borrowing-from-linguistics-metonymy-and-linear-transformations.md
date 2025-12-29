---
layout: post
title: '[RUME 2016] Borrowing from linguistics: Metonymy and linear transformations'
categories:
- sbagleyteaches
---


Here's part 2 of my "borrowing from linguistics" series.




So like I said in [yesterday's post](https://sbagleyteaches.wordpress.com/2016/03/02/rume-2016-borrowing-from-linguistics-rina-zazkis-and-the-superscript-1/), Rina Zazkis's talk grabbed my attention because of some [previous work](https://www.researchgate.net/publication/270596078_Inverse_composition_and_identity_The_case_of_function_and_linear_transformation) I've done. (Some day I will bother to make my own personal website and link to things there, but that day is not today.) My coauthors on that paper, Chris Rasmussen and Michelle Zandieh, had conducted these interesting interviews on students' construal of similarity between linear transformations and functions like from high-school algebra. These interviews were wide-ranging, including such topics as injectivity, surjectivity, invertibility, and composition. I focused in on the bits about invertibility and composing a function / linear transformation with its inverse.




One of the tasks from those interviews was to predict what you'd get when you compose a function with its inverse, and then to predict what you'd get when you compose a linear transformation with its inverse. When I started digging into this data, I noticed something unexpected: all ten students initially said you should get 1 in the function case -- i.e., that $ f(f^{-1}(x))$ should be 1. This seemed weird, and it drove the investigation that turned into this paper: why did everyone make this incorrect prediction??




One of the things that ended up being salient was that many of these students predicted that a linear transformation composed with its inverse should be the identity matrix (i.e., that $ \mathbf{T}(\mathbf{T}^{-1}(\mathbf{x})) = \mathbf{I}$). This seems less weird and more understandable. The place where *this* comes from, we ended up arguing in the paper, is a *metonymy.*




Let's digress a bit and recall what [metonymy](https://en.wikipedia.org/wiki/Metonymy) is. For our purposes, metonymy is a literary device whereby a thing is called not by its name, but by the name of one of its parts\*, or by the name of something that is associated with it. For instance, you can use "Hollywood" to refer to the American movie industry, or "the press" (i.e., the printing press) to refer broadly to the journalistic endeavor. (These examples are gratuitously stolen from the Wikipedia page).




What's the metonymy that's going on here? It's actually very mathematically sophisticated: Every linear transformation from $ \mathbf{R}^n$ to $ \mathbf{R}^m$ can be represented as a particular $ m \times n$ matrix. (What's more, every matrix represents a linear transformation, so that Hom($ \mathbf{R}^n$, $ \mathbf{R}^m$) is in fact isomorphic (as a vector space) to $ \mathbf{M}\_{m\times n}$! This isomorphism is canonical as long as you're working in the standard bases for $ \mathbf{R}^n$ and $ \mathbf{R}^m$.) We make use of this fact all the time: we usually write $ \mathbf{T}(\mathbf{x}) = \mathbf{A}\cdot\mathbf{x}$ whenever we're discussing some transformation.




Now here's the metonymy: we tend to speak of the matrix $ \mathbf{A},$ which *represents* the transformation, *as* the transformation -- for instance, it's not unusual to say that $ \mathbf{A} = \begin{pmatrix} \cos\theta & -\sin\theta \\ \sin\theta & \cos\theta \end{pmatrix}$ *is* a CCW rotation by an angle $ \theta$. However, it would be more accurate to say that $ \mathbf{A}$ *represents* such a transformation. For mathematically sophisticated people, this little bit of playing fast and loose is not really problematic, and in fact it enables fluency that is a mark of mathematical sophistication. (If I need to calculate the composition of two transformations, I can quickly and fluently pass into thinking about multiplying the two matrices, and then quickly and fluently pass back into thinking about the resulting matrix as representing the resulting transformation.) However, for our students, it can cause trouble, as I'll detail below.




Let's think about composing a transformation with its inverse: $ \mathbf{T}(\mathbf{T^{-1}}(\mathbf{x})) = \mathbf{A}\cdot(\mathbf{A}^{-1}\cdot\mathbf{x}) = \mathbf{I}\cdot\mathbf{x} = \mathbf{x}.$ (Note that this calculation sort of implicitly invoked the isomorphism discussed above.) Not so bad, right?




But now let's really buy into this metonymy and try that again:




$ \mathbf{T}(\mathbf{T^{-1}}(\mathbf{x})) \leadsto \mathbf{A} \cdot \mathbf{A}^{-1} = \mathbf{I}.$




Hm. That's *slightly* wrong. And, as I'm sure any of you who teach linear algebra will immediately recognize, lots of students do this. It's not a big deal as long as you remember to "un-metonymize" and stick that $ \mathbf{x}$ back on the end, and mathematically sophisticated people do this fluently. However, if you're not super aware that this is a metonymy, and you just think that the matrix *is* the transformation, then this could lead to problems.




In particular, it could lead you to say something like, "if I compose a linear transformation with its inverse, I ought to get the identity matrix," which is indeed something that a lot of people in our interviews said. And again, this is wrong, but maybe only *slightly* wrong. If you compose a linear transformation with its inverse, you get a transformation that is *represented* by the identity matrix, i.e., the identity transformation $ \mathbf{T}(\mathbf{x}) = \mathbf{x}$.




So I think this is another example of a productive borrowing from linguistics: the word "metonymy" is probably a good one to have in our conceptual toolboxes when we're teaching linear algebra. I'm not going to say that telling students about this whole metonymy thing is going to 100% keep them from making this mistake, but I think it might help. At the very least, it gives us a conceptual label for this tricky subject that doesn't require an understanding of isomorphisms of vector spaces.




Anyway, with this train of thought in mind, it's sorta unsurprising that people say that they should get 1 if they compose a function with its inverse. 1 is kinda like $ \mathbf{I}$ (in that they are both the multiplicative identity in their respective rings), so maybe this new "fact" that comes from thinking metonymously in linear algebra is influencing an old thing they used to know -- which leads us to *backward transfer*, the subject of a future blog post!




---------------




\* Some sticklers will probably here insist that a part-whole relationship is a synecdoche rather than a metonymy. I prefer to consider synecdoche a particular kind of metonymy. If this bothers you, then feel free to mentally alter my terms; I don't think it will impact the argument.



