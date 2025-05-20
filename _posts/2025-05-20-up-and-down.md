---
layout: post
title:  "Up and down the subgroup lattice"
tags: teaching math pqr
katex: true
---

This post is part of a three-post set 
([1]({% link _posts\2025-05-20-weird-proofs.md %}) 
 [2]({% link _posts\2025-05-20-up-and-down.md %})
 [3]({% link _posts\2025-05-20-pqr-groups.md %})
)
about groups of order $pqr$, where $p<q<r$ are prime. 
While thinking about such $pqr$-groups, I've collected a bunch of theorems and lemmas into a little mental toolbox. An interesting commonality between a lot of these tools is that they tell us about the relationship between various different animals in the subgroup lattice; an interesting *difference* is that some of them go "upwards," some of them go "downwards,"[^1] and some of them even go "sideways."

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

**Vanishing quotient theorem**: If $G/Z(G)$ is cyclic, then $G$ is abelian, and thus $G/Z(G)$ is trivial. Immediate corollaries:
- $G/Z(G)$ can't be nontrivial cyclic.
- $Z(G)$ can't have prime index.

The moral of this result is that $Z(G)$ can't be too high in the subgroup lattice (unless of course it is $G$ itself!). The upper reaches of the subgroup lattice are populated by things of small index; the smallest indices you can get are prime divisors of $|G|$; if $Z(G)$ was up there then its quotient would be $\mathbb{Z}_p$. So this one makes for "downward pressure" on the location of $Z(G)$.

**Normal-parent lemma**: Suppose that $H\leq N \unlhd G$. If $\newcommand\cl{\operatorname{cl}} K\in \cl_G(H)$, then $K \leq N$. ("Conjugacy classes stay within normal parents.")

*Proof*: Pick some $x\in G$ and consider the conjugate subgroup $\newcommand\inv{^{-1}} xHx\inv$. We'd like to show that this is a subgroup of $N$. Pick some $h\in H$; where does it go when you conjugate? Well, since $H \leq N$, $h$ is an element of $N$, so $xhx\inv$ is an element of $xNx\inv$, but hey, that's just $N$ again. 

## Upwards

Here are some theorems that go "up" the subgroup lattice: given information about a subgroup (or *some* subgroups), what can you say about its parents?

**$AB$ lemma**: Let $A, B \leq G$. If $B\unlhd G$, then $AB := \{ab\mid a\in A, b\in B\}$ is a subgroup of $G$, and $|AB| = \dfrac{|A|\cdot|B|}{|A\cap B|}.$

Further, $B$ doesn't have to be fully normal in $G$; you can weaken this hypothesis to say that $B$ is normalized by $A$, ie., $A\leq N_G(B)$. In this case, we can further conclude that $B \triangleleft AB$.

To my point about going upwards, note that both $A$ and $B$ are subgroups of $AB$, so $AB$ lives somewhere "above" both $A$ and $B$ in the subgroup lattice.

*Idea of proof*: This is a pretty straightforward exercise in verifying that something is a subgroup. A key idea is that normal subgroups are "almost central" -- since $aB = Ba$, $a \cdot b = b' \cdot a$, even if $ab \neq ba$. This means that the multiplication within $AB$ works how you want it to.

**Normalizer lemma**: $H\leq N_G(H) \leq G$ ("the normalizer of $H$ lives somewhere above $H$ in the subgroup lattice"), and thus $[G:H] = [G:N_G(H)]\cdot [N_G(H):G]$.

*Idea of proof*: The first part is a good exercise in proving something is a subgroup of something else; the second part is a consequence of Lagrange's theorem slash the tower law.

The next one is a good friend of the normalizer lemma:

**Class lemma**: Let $H\leq G$. Then $|\cl_G(H)| = [G: N_G(H)]$ ("the number of conjugate subgroups of $H$ is the same as the index of its normalizer").

*Idea of proof*: This is a direct consequence of the orbit-stabilizer theorem, but you can also prove it directly by establishing a bijection between conjugates of $H$ and cosets of its normalizer.

The normalizer lemma and the class lemma pair nicely together, particularly in a certain Goldilocks zone. If your subgroup's conjugacy class is too small, then your subgroup is normal and thus its normalizer is all the way at the top of the lattice. If your subgroup's conjugacy class is too big, then your subgroup is "fully un-normal," ie., only normalized by itself. But if your subgroup's conjugacy class is juuuuust right, you can force a nontrivial chain of inclusions going up the subgroup lattice. Sometimes this is a way to prove that there must exist subgroups of intermediate order in your big group.

## Sideways

Here are some theorems that talk about how things propagate "across" the subgroup lattice to inform you about the properties of other sbugroups of the same order.

**Class multiplication lemma**: Say that $H \leq K \leq G$. Then $|\cl_G(H)| = |\cl_K(H)| \cdot |\cl_G(K)|.$ (The size of conjugacy classes multiplies how you wish it would.)

*Tongue-in-cheek proof*: Conjugation is an isomorphism. \qed

*Slightly more detailed proof*: Below every conjugate of $K$, there's an exact copy of the entire subgroup lattice of $K$ ("isomorphisms send subgroups to subgroups"). In particular, there's an exact copy of the entire ($K$-)conjugacy class of its subgroup $H$ ("isomorphisms send conjugates to conjugates"). And, crucially, there's no other $G$-conjugates of $H$, because any $G$-conjugate of $H$ has to be some subgroup of a $G$-conjugate of $K$. And we're done!

(Btw, the "normal parent lemma" from earlier is a direct corollary of this one.)

**Correspondence Theorem** (aka the $n$-th isomorphism theorem, where $n$ is either 2, 3, or 4 depending on which book you are looking at): Suppose that $N \unlhd G$. There is a **correspondence** between subgroups of $G/N$ and subgroups of $G$ that contain $N$, under which everything you want to be true is in fact true.

*Idea of proof*: The canonical quotient map $\pi: G \to G/N$ ends up respecting pretty much every property you can think of.

Why am I calling this one "sideways"? Precisely because you can take what you know about the lattice of $G/N$ and pull it back across ("sideways") to the portion of the lattice of $G$ that lives above $N$. 

## Lasers

Sometimes, by combining upwards and downwards theorems in a clever way, you can end up with really powerful results. Reminds me of a laser: each time your argument bounces back and forth, it gains power.


[^1]: If you have an opinion about "downward" vs. "downwards," that is very nice but I don't actually care. <3