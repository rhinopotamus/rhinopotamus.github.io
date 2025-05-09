---
layout: post
title:  "Up and down the subgroup lattice"
tags: teaching math
katex: true
---

I've been thinking a lot about a fun problem in group theory lately, and I've thus collected a bunch of theorems and lemmas into a little mental toolbox. An interesting commonality between a lot of these tools is that they tell us about the relationship between various different animals in the subgroup lattice; an interesting difference is that some of them go "upwards" and some of them go "downwards."[^1]

## Downwards

Here are some theorems that go "down" the subgroup lattice: given information about a group (or subgroup), what can you say about its subgroups?

**Sylow theorems** : Let $G$ be a finite group and let $p^n$ be the highest power of $p$ dividing $|G|$, so that $|G| = p^n \cdot m$, where $m$ is relatively prime to $p$. Then:
1. There exists a subgroup of $G$ of order $p^n$, which is called a *Sylow $p$-subgroup*.
    - Furthermore, there also exist subgroups of order $p^m$ for all $m<n$, and they are "nested" in a "$p$-group tower" with the Sylow $p$-subgroup(s) at the top.
2. Any two Sylow $p$-subgroups are conjugate and thus isomorphic; there is thus a single conjugacy class of Sylow $p$-subgroups.
3. The number of Sylow $p$-subgroups, which we'll call $n_p$, is:
    - congruent to 1 mod $p$,
    - the index of the normalizer of the Sylow $p$-subgroup, and thus
    - a divisor of $m$.

This is sort of the biggest and most powerful of all the "downward" theorems. Just by knowing the prime factorization of the order of a group, you know the whole bottom of the subgroup lattice is populated by $p$-subgroup towers each capped off by one conjugacy class of maximal $p$-subgroups.

**Small-index lemma**: If $p$ is the smallest prime dividing $|G|$, and $H\leq G$ such that $[G:H] = p$, then $H \unlhd G$. (A familiar corollary is that any subgroup of index 2 must be normal.)

*Idea of proof*: Let $G$ act on the cosets of $H$ by multiplication; let $K$ be the kernel of the action; look at the lattice of $G/K$; use the correspondence theorem to see that $[H:K] = 1$. Love a good group action; love the correspondence theorem.

**I need to think of a cute name for this one**: If $G/Z(G)$ is cyclic, then $G$ is abelian, and thus $G/Z(G)$ is trivial. Immediate corollaries:
- $G/Z(G)$ can't be nontrivial cyclic.
- $Z(G)$ can't have prime index.

The moral of this result is that $Z(G)$ can't be too high in the subgroup lattice (unless of course it is $G$ itself!). The upper reaches of the subgroup lattice are populated by things of small index; the smallest indices you can get are prime divisors of $|G|$; if $Z(G)$ was up there then its quotient would be $\mathbb{Z}_p$. So this one makes for "downward pressure" on the location of $Z(G)$.

**Normal-parent lemma**: Suppose that $H\leq N \unlhd G$. If $\newcommand\cl{\operatorname{cl}} K\in \cl_G(H)$, then $K \leq N$. ("Conjugacy classes stay within normal parents.")

*Proof*: Pick some $x\in G$ and consider the conjugate subgroup $\newcommand\inv{^{-1}} xHx\inv$. We'd like to show that this is a subgroup of $N$. Pick some $h\in H$; where does it go when you conjugate? Well, since $H \leq N$, $h$ is an element of $N$, so $xhx\inv$ is an element of $xNx\inv$, but hey, that's just $N$ again. 

## Upwards

Here are some theorems that go "up" the subgroup lattice: given information about a subgroup (or *some* subgroups), what can you say about its parents?

**$AB$ lemma**: Let $A, B \leq G$. If $A\unlhd G$, then $AB := \{ab\mid a\in A, b\in B\}$ is a subgroup of $G$, and $|AB| = \dfrac{|A|\cdot|B|}{|A\cap B|}.$

To my point about going upwards, note that both $A$ and $B$ are subgroups of $AB$, so $AB$ lives somewhere "above" both $A$ and $B$ in the subgroup lattice. Also worth noting that $A$ doesn't have to be fully normal in $G$; you can weaken this hypothesis to say that $A$ is normalized by $B$, ie., $B\leq N_G(A)$.

*Idea of proof*: This is a pretty straightforward exercise in verifying that something is a subgroup. A key idea is that normal subgroups are "almost central" -- since $bA = Ab$, $b\cdot a = a' \cdot b$, even if $ba \neq ab$. This means that the multiplication within $AB$ works how you want it to.

**Normalizer lemma**: $H\leq N_G(H) \leq G$ ("the normalizer of $H$ lives somewhere above $H$ in the subgroup lattice"), and thus $[G:H] = [G:N_G(H)]\cdot [N_G(H):G]$.

*Idea of proof*: The first part is a good exercise in proving something is a subgroup of something else; the second part is a consequence of Lagrange's theorem slash the tower law.

The next one is a good friend of the normalizer lemma:

**Class lemma**: Let $H\leq G$. Then $|\cl_G(H)| = [G: N_G(H)]$ ("the number of conjugate subgroups of $H$ is the same as the index of its normalizer").

*Idea of proof*: This is a direct consequence of the orbit-stabilizer theorem, but you can also prove it directly by establishing a bijection between conjugates of $H$ and cosets of its normalizer.

The normalizer lemma and the class lemma pair nicely together, particularly in a certain Goldilocks zone. If your subgroup's conjugacy class is too small, then your subgroup is normal and thus its normalizer is all the way at the top of the lattice. If your subgroup's conjugacy class is too big, then your subgroup is "fully un-normal," ie., only normalized by itself. But if your subgroup's conjugacy class is juuuuust right, you can force a nontrivial chain of inclusions going up the subgroup lattice. Sometimes this is a way to prove that there must exist subgroups of intermediate order in your big group.

## Sideways

**Class multiplication lemma**: Say that $H \leq K \leq G$. Then $|\cl_G(H)| = |\cl_K(H)| \cdot |\cl_G(K)|.$ (The size of conjugacy classes multiplies how you wish it would.)

*Tongue-in-cheek proof*: Conjugation is an isomorphism. \qed

*Slightly more detailed proof*: For each $x\in G$, let $\phi_x(g) = xgx\inv$ be conjugation by $x$; this is an isomorphism. Say that $K' = xKx\inv = \phi_x(K)$. Since $\phi_x$ is an isomorphism, it sends subgroups to subgroups, so $\phi_x(H) \leq K'$. Therefore, within each distinct conjugate of $K$, there is an isomorphic image of $H$, say $H'$.

What's more, since $\phi_x$ is a homomorphism, it respects conjugation. Suppose that $H_k= kHk\inv$ is a conjugate of $H$ within $K$. Then $\phi_x(H_k) = \phi_x(kHk\inv) = \phi_x(k)\ \phi_x(H)\ \phi_x(k)\inv = \phi_x(k)\ H'\ \phi_x(k)\inv$, so the image of $H_k$ is a conjugate within $K'$ of the image of $H$. 

So, below every conjugate of $K$, there's a fresh copy of the entire ($K$-)conjugacy class of its subgroup $H$. And, crucially, there's no other $G$-conjugates of $H$, because any $G$-conjugate of $H$ has to be some subgroup of a $G$-conjugate of $K$. And we're done!

(Btw, the "normal parent lemma" from earlier is a direct corollary of this one.)

## Lasers

Up-down-up-down -> very powerful results


[^1]: If you have an opinion about "downward" vs. "downwards," that is very nice but I don't actually care. <3