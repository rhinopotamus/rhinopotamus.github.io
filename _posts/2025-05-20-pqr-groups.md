---
layout: post
title:  "$pqr$-groups"
tags: teaching math pqr
katex: true
---

This post is part of a three-post set 
([1]({% post_url 2025-05-20-weird-proofs %}) 
 [2]({% post_url 2025-05-20-up-and-down %})
 [3]({% post_url 2025-05-20-pqr-groups %}))
about groups of order $pqr$, where $p<q<r$ are prime. 
While designing final exam questions for my group theory class, I was [playing around with groups of order 42](https://bsky.app/profile/sbagley.bsky.social/post/3lojgjg6x6k2t), for [no particular reason](https://en.wikipedia.org/wiki/Phrases_from_The_Hitchhiker%27s_Guide_to_the_Galaxy#_The_Answer_to_the_Ultimate_Question_of_Life,_the_Universe,_and_Everything_is_42), and then [a friend noticed something interesting](https://bsky.app/profile/visualalgebra.bsky.social/post/3lojmnaokxs2l) that I wanted to try to prove more generally. Here's a complete writeup of this proof. Is it the most beautiful and elegant proof? Certainly not; you can directly quote some results about [groups of square-free order being supersolvable](https://en.wikipedia.org/wiki/Supersolvable_group), but I think this approach is pedagogically useful.

## $pqr$-groups

The interesting thing about the number 42, in this context, is that it's the product of three distinct primes: $42 = 2\cdot 3\cdot 7$. It's a common exercise in a group theory class to play around with the similar number $30 = 2\cdot 3 \cdot 5$; indeed, Dummit & Foote present this as a main example of applications of the Sylow theorems. Specifically, D&F prove that a group of order 30 has a normal subgroup isomorphic to $\mathbb{Z}_{15}$. Turns out you can extend their argument[^1] and say something more general:

**$pqr$ theorem**: Let $G$ be a group of order $pqr$, where $p<q<r$ are primes. Then:
1. $G$ has a subgroup of every order dividing $pqr$.
2. The subgroup of order $r$ is normal (indeed, characteristic).
3. The subgroup of order $qr$ is normal (indeed, characteristic).
4. There is just one conjugacy class of subgroups of each order.

### Lemmas

The post about [going up and down the subgroup lattice]({% post_url 2025-05-20-up-and-down %}) contains a bunch of lemmas that I'm stapling together to streamline the presentation of this proof; it's fun to notice just how many times the proof uses each of these.

I'll just add one more thing here that I don't really think of as either "upwards" or "downwards" (or indeed "sideways"):

**$pq$-group theorem**: If a group $G$ has order $pq$, where $p<q$ are prime, the $q$-Sylow subgroup is normal, and $G$ is either a direct product $C_p\times C_q$ and thus cyclic, or, in the case that $p\mid q-1$, a semidirect product $C_q\rtimes C_p$.

*Idea of proof*: Apply the Sylow theorems and then notice that $\operatorname{Aut}(C_q) = C_{q-1}$.

## Proof of the $pqr$ theorem

Let $P$ be a Sylow $p$-subgroup of $G$, and $Q$ and $R$ similar. 

**Part 2** (yes, this is before Part 1, deal with it): As established in [the post about weird proofs]({% post_url 2025-05-20-weird-proofs %}), $R$ is normal (characteristic!) in $G$. 

**Part 1:** $G$ has subgroups of every possible order, ie., $p$, $q$, $r$, $pq$, $pr$, and $qr$. 

$P$, $Q$, and $R$ are subgroups of orders $p$, $q$, and $r$, respectively, so now we just need to prove the existence of the subgroups of composite order.

By the $AB$ lemma, since $R$ is normal, $PR$ and $QR$ are subgroups of $G$ of orders $pr$ and $qr$ respectively; the only order we haven't thus covered is $pq$. 

Let's zoom in on the subgroup $QR$. First, we'll note that $[Q:QR] = \dfrac{pqr}{qr} = p$, so by the small-index lemma, $QR$ is normal in $G$, so we're (almost) done with **Part 3**. (We'll have to wait a bit to show $QR$ is characteristic.)

Since $Q < QR$, $Q$ is in fact a $q$-Sylow subgroup of $QR$! Therefore, within $QR$, either $n_q = 1$ or $n_q = r$. This is an improvement over the situation in the big group $G$, in which $n_q$ could, a priori, possibly be $pr$.

But wait, could it be the case that $n_q = r$ within $QR$, but then when we go back out to the big group, $n_q = pr$? Turns out that no, because $QR$ is normal, so the normal-parent lemma tells us that $Q$'s whole conjugacy class (in $G$!) consists of subgroups of $QR$. Further, the Sylow theorems tell us that all the $q$-Sylow subgroups come in just one conjugacy class. 

So, even when we pass back out to the big group $G$, $n_q = 1$, in which case $Q$ is normal and $PQ$ is a subgroup of $G$, or $n_q = r$, in which case we can apply the class lemma to say that's the index of its normalizer $N_G(Q)$, so the order of the normalizer is $\vert G\vert  / r = pq$. Yay, either way, we get a group of order $pq$, and we've completed Part 1 of the theorem.

**Part 4**: There is just one conjugacy class of subgroups of each order.

For orders $p$, $q$, and $r$, this follows directly from the Sylow theorems. Let's therefore step through the composite orders.

*Order $qr$*: Since $R$ is normal, let's go look at $G/R$ and apply the correspondence theorem. $G/R$ has order $\dfrac{pqr}{r} = pq$ and thus has a normal Sylow $q$-subgroup, which must be $QR/R$ and which thus must correspond with $QR$ above $R$ in the lattice of $G$. Therefore, $QR$ is the *unique* subgroup of order $qr$, and is characteristic in $G$. (Therefore we're also done with **Part 3** now!)

*Order $pr$*: Similarly, $G/R$ must have a single conjugacy class of $p$-Sylow subgroups. By the correspondence theorem, one of these $p$-Sylow subgroups must be $PR/R$, which means that we can pull back the single conjugacy class of $PR/R$ within $G/R$ to a single conjugacy class of $PR$ within $G$.

*Order $pq$*: This argument goes slightly different ways depending on whether or not $Q$ is normal in $G$. If $Q$ is normal, then $P_iQ$ is a subgroup of order $pq$ for each $p$-sylow subgroup $P_i < G$. What's more, any subgroup $H$ of order $pq$ must contain a $p$-Sylow subgroup $P_H$, so $P_H Q  \leq H$, so for order reasons $P_HQ = H$ -- that is, every subgroup of order $pq$ is of the form $P_i Q$ for some Sylow $p$-subgroup $P_i$. Since all the $p$-Sylow subgroups are conjugate, all these $P_iQ$'s are conjugate (because $x(PQ)x^{-1} = (xPx^{-1})Q$).

So now let's say $Q$ is not normal in $G$. Any subgroup $H$ of order $pq$ must have a normal $q$-Sylow subgroup $Q_H \triangleleft H$, so $H \leq N_G(Q_H)$. Furthermore, for order reasons, $H=N_G(Q_H)$; this is to say that any subgroup of order $pq$ is the normalizer of a $q$-Sylow subgroup of $G$. Letting $G$ act on its subgroups by conjugation, and observing that stabilizers of elements in the same orbit are conjugate, we conclude that all these normalizers are conjugate, ie., every subgroup of order $pq$ is conjugate.

## Counterexamples to everything else

A fun thing about the number $42 = 2\cdot 3 \cdot 7$ that I originally was playing around with is that there is a group of order 42 that is a counterexample to everything else you might reasonably conjecture.
- The subgroup of order $pq$ is not necessarily normal; [the Frobenius group](https://beta.lmfdb.org/Groups/Abstract/42.1) $F_7$ has a conjugacy class of 7 copies of $C_6$.
- The subgroup of order $pr$ is not necessarily normal; [the direct product](https://beta.lmfdb.org/Groups/Abstract/42.3) $S_3 \times C_7$ has a conjugacy class of 3 copies of $C_{14}$.
- There's nothing specific you can say about $n_p$: 
    - in [the cyclic group](https://beta.lmfdb.org/Groups/Abstract/42.6) $C_{42}$ it is of course 1, and it is also 1 in [the semidirect product](https://beta.lmfdb.org/Groups/Abstract/42.2) $C_7 : C_6$ so you can't even make a claim about abelian groups, 
    - in [the direct product](https://beta.lmfdb.org/Groups/Abstract/42.3) $S_3 \times C_7$ it is 3,
    - in [the Frobenius group](https://beta.lmfdb.org/Groups/Abstract/42.1) $F_7$ it is 7,
    - and in [the dihedral group](https://beta.lmfdb.org/Groups/Abstract/42.5) $D_{21}$ it is 21.

## What's next?

I'm going to hit publish on this whole project now, but I do have a couple of ideas about next steps:
- None of these posts contain any pictures, which is a damn shame bc subgroup lattices have been instrumental in my thought process. I intend to fix this.
- I think you could build a fun problem sequence out of this, to run alongside a couple weeks of an algebra course. All the lemmas are pretty accessible and touch on a surprising variety of stuff. I might try my hand at this.


[^1]: A key part of the D&F argument relies on something that is not true for general $pqr$ (indeed, it's not true for 42). It took me an embarassingly long time to disentangle this.

[^2]: Furthermore, there exist subgroups of order $p^k$ for all $k < n$, and all of them are "nested subgroups" of the Sylow $p$-subgroup(s).