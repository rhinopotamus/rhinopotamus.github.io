---
layout: post
title: A combinatorics thing
categories:
- sbagleyteaches
---


So, a while back, a student did a thing in discrete, which was wrong in an interesting way, and I wanted it to be simpler to get to the right thing than it was, which made me think a lot about what happened. Here we go.




I thought about this some today because I didn't want to grade, so I gave myself the Friday-afternoon gift of some fun math.




The problem was like, distribute 5 votes across 21 learning targets, but you can vote for the same thing multiple times. The answer is $ \displaystyle \binom{5+21-1}{5} = \binom{25}{5}$, which you get by sticks and stones. The student said $ 21^5$, which makes sense if the votes are distinguishable and the order matters. So, it seems like you should be able to just divide $ 21^5$ by something having to do with reordering stuff to get $ \displaystyle\binom{25}{5}$. However, numerically speaking, this doesn't work: $ 21^5 = 4084101$, while $ \displaystyle\binom{25}{5} = 53130$, and that doesn't divide evenly -- you get some dumb thing like 76.87.




Hm. 




I don't really know how to tackle this because 21 is an obnoxiously large number. I think I need to think about this with a smaller number. Like, 2. That should be small enough.




So I want to distribute 5 votes across 2 learning targets. Maybe I want to think about this as something to do with $ (x+y)^5$. I think this is good -- I can think about, say, $ x^3 y^2$ as giving 3 votes to x and 2 votes to y. I also like this because it provides a link between $ 2^5$ -- which is the sum of all the binomial coefficients -- and the stars-and-bars thing $ \displaystyle\binom{6}{1}$ -- which is the number of terms in the binomial expansion.




Another thing I can count with binomial coefficients is bit strings of length 5. Say that if a bit string has k 1's in it, then it has weight k. Then $ \displaystyle\binom{5}{k}$ is the number of bit strings of length 5 and weight k. This got me thinking about equivalence relations.




Say that B is the set of all bit strings of length 5. Define a relation called ~ on B by saying that a ~ b if a and b have the same weight. It's reasonably easy to see that this is in fact an equivalence relation, and then the equivalence classes are precisely the different weights. (So in some sense, B / ~ is like the set {1, \ldots, 5}.)




This lets me see the reason why you can't just divide by something nice: the equivalence classes aren't all the same size. There's way more ways to get to $ x^2y^3$ than there are to get to $ x^5y^0$. 




Okay, so next on the list, and I haven't quite done this yet, is to think about this back in the case of 21 learning targets. Then we're looking at, like, $ \displaystyle\left(\sum\_{i=1}^{21} x\_i\right)^5$; instead of binary strings, we have 21-ary strings of length 5; and then you look at the equivalence classes of ~ and see that there's $ \displaystyle\binom{25}{5}$ of them (by sticks and stones; and then B / ~ is like the set of ordered 21-tuples where all the entries add up to 5. But you still have the same issue where the equivalence classes aren't all the same size. I don't know how big each one is yet -- this seems like a good job for multinomial coefficients. 




Which, don't those just come from the higher-dimensional version of Pascal's triangle? Like, 3nomial coefficients come from "Pascal's cube" or whatever. And then Pascal's triangle just lives on the face of Pascal's cube. So if you take some *other* 2-dimensional slice of Pascal's hypercube, do you get something interesting? Maybe it's a thing that shows us a more direct link between $ 21^5$ and $ \displaystyle\binom{25}{5}$?




Anyway, this was fun and interesting and I'm excited to think about it more.



