---
layout: post
title:  "$pqr$-groups"
tags: teaching math
katex: true
---

While designing final exam questions for my group theory class, I was [playing around with groups of order 42](https://bsky.app/profile/sbagley.bsky.social/post/3lojgjg6x6k2t), for [no particular reason](https://en.wikipedia.org/wiki/Phrases_from_The_Hitchhiker%27s_Guide_to_the_Galaxy#_The_Answer_to_the_Ultimate_Question_of_Life,_the_Universe,_and_Everything_is_42), and then [a friend noticed something interesting](https://bsky.app/profile/visualalgebra.bsky.social/post/3lojmnaokxs2l) that I wanted to try to prove more generally. Here's a complete writeup of this proof.

## $pqr$-groups

The interesting thing about the number 42, in this context, is that it's the product of three distinct primes: $42 = 2\cdot 3\cdot 7$. It's a common exercise in a group theory class to play around with the similar number $30 = 2\cdot 3 \cdot 5$; indeed, Dummit & Foote present this as a main example of applications of the Sylow theorems. Specifically, D&F prove that a group of order 30 has a normal subgroup isomorphic to $\mathbb{Z}_{15}$. Turns out you can extend their argument[^1] and say something more general:

**$pqr$ theorem**: Let $G$ be a group of order $pqr$, where $p<q<r$ are primes. Then:
1. $G$ has a subgroup of every order dividing $pqr$.
2. The subgroup of order $qr$ is normal (indeed, characteristic).
3. There is just one conjugacy class of subgroups of each order.

### Lemmas

It'll be helpful to establish a couple of lemmas to streamline the presentation of this proof; it's fun to notice just how many times the proof uses each of these. I'm not going to write full proofs of each of these lest the blog post become a novel, but I'll try to say at least some ideas for each one.

**Sylow theorems** (not a lemma): Let $G$ be a finite group and let $p^n$ be the highest power of $p$ dividing $|G|$, so that $|G| = p^n \cdot m$, where $m$ is relatively prime to $p$. Then:
1. There exists a subgroup of order $p^n$, which is called a *Sylow $p$-subgroup*.[^2] 
2. Any two Sylow $p$-subgroups are conjugate and thus isomorphic.
3. The number of Sylow $p$-subgroups, which we'll call $n_p$, is:
    - congruent to 1 mod $p$,
    - the index of the normalizer of the Sylow $p$-subgroup, and thus
    - a divisor of $m$.

This is a key piece of machinery for any kind of "classify all groups of order $n$" kind of argument. The proof of each part is basically, think of a cute group action and show that it works nicely for groups of prime power order.

**$AB$ lemma**: Let $A, B \leq G$. If $A\unlhd G$, then $AB := \{ab\mid a\in A, b\in B\}$ is a subgroup of $G$, and $|AB| = \dfrac{|A|\cdot|B|}{|A\cap B|}.$

*Idea*: This is a pretty straightforward exercise in verifying that something is a subgroup. A key idea is that normal subgroups are "almost central" -- since $bA = Ab$, $b\cdot a = a' \cdot b$, even if $ba \neq ab$. This means that the multiplication within $AB$ works how you want it to.

**Class lemma**: Let $H\leq G$. Then $\newcommand\cl{\operatorname{cl}} |\cl_G(H)| = [G: N_G(H)]$ ("the number of conjugate subgroups of $H$ is the same as the index of its normalizer").

*Idea*: This is a direct consequence of the orbit-stabilizer theorem, but you can also prove it directly by establishing a bijection between conjugates of $H$ and cosets of its normalizer.

**Normalizer lemma**: $H\leq N_G(H) \leq G$ and thus $[G:H] = [G:N_G(H)]\cdot [N_G(H):G]$.

*Idea*: The first part is a good exercise in proving something is a subgroup of something else; the second part is a consequence of Lagrange's theorem slash the tower law.

**Small-index lemma**: If $p$ is the smallest prime dividing $|G|$, and $H\leq G$ such that $[G:H] = p$, then $H \unlhd G$.

*Idea*: Let $G$ act on the cosets of $H$ by multiplication; let $K$ be the kernel of the action; look at the lattice of $G/K$; use the correspondence theorem to see that $[H:K] = 1$. Love a good group action; love the correspondence theorem.

**Normal-parent lemma**: Suppose that $H\leq N \unlhd G$. If $K\in \cl_G(H)$, then $K \leq N$. ("Conjugacy classes stay within normal parents.")

*Proof*: Pick some $x\in G$ and consider the conjugate subgroup $\newcommand\inv{^{-1}} xHx\inv$. We'd like to show that this is a subgroup of $N$. Pick some $h\in H$; where does it go when you conjugate? Well, since $H \leq N$, $h$ is an element of $N$, so $xhx\inv$ is an element of $xNx\inv$, but hey, that's just $N$ again. 

### Proof of the $pqr$ theorem

Ok, now we have all the pieces we need! Let $P$ be a Sylow $p$-subgroup of $G$, and $Q$ and $R$ similar.

**Part 1:** $G$ has subgroups of every possible order, ie., $p$, $q$, $r$, $pq$, $pr$, and $qr$. 

We'll break up this argument into a couple of cases.

*Case 1:* $R$ is not normal in $G$. What could $n_r$ be? It has to be a divisor of $pq$ and it can't be 1, otherwise $R$ would be normal. Therefore it must be $pq$ (it can't be $p$ or $q$ because neither of those is big enough to be 1 mod $r$). Well, that's a lot of elements of order $r$ -- specifically, since each conjugate of $R$ contains $r-1$ elements of order $R$ and all the conjugates of $R$ intersect trivially, there are $pq \cdot (r-1) = pqr - pq$ elements of order $R$. But there's only $pqr$ total elements in the whole group! So there's only $pq$ elements left over to have order not-$r$, which is just enough space for one copy of $P$ and one copy of $Q$. Hence, both $P$ and $Q$ are normal, so by the $AB$ lemma, $PQ$, $PR$, and $QR$ are subgroups of $G$. And since $P$, $Q$, and $R$ intersect trivially (for order reasons), $|PQ| = pq$, $|PR| = pr$, and $|QR| = qr$.  

ANNOYING: turns out that R is normal anyway because then it's a r-sylow subgroup of QR, so normal in QR, so char in QR, so normal in G.

*Case 2:* Ok, so now suppose $R\unlhd G$. By the $AB$ lemma, $PR$ and $QR$ are subgroups of $G$ of orders $pr$ and $qr$ respectively; the only order we haven't thus covered is $pq$. 

Let's zoom in on the subgroup $QR$. Since $Q < QR$, $Q$ is in fact a $q$-Sylow subgroup of $QR$! Therefore, within $QR$, either $n_q = 1$ or $n_q = r$. This is an improvement over the situation in the big group $G$, in which $n_q$ could, a priori, possibly be $pr$.

But wait, could it be the case that $n_q = r$ within $QR$, but then when we go back out to the big group, $n_q = pr$? Turns out that no, because $QR$ is normal by the small-index lemma, so the normal-parent lemma tells us that $Q$'s whole conjugacy class (in $G$!) consists of subgroups of $QR$. Further, the Sylow theorems tell us that all the $q$-Sylow subgroups come in just one conjugacy class. 

So, even when we pass back out to the big group $G$, $n_q = 1$, in which case $Q$ is normal and $PQ$ is a subgroup of $G$, or $n_q = r$, in which case we can apply the class lemma to say that's the index of its normalizer, so the order of the normalizer is $|G| / r = pq$. Yay, either way, we get a group of order $pq$, and we've completed Part 1 of the theorem.

**Part 2**: The subgroup of order $qr$ is normal (indeed, characteristic).

This follows directly from the existence of a subgroup of order $QR$ and the small-index lemma. (We'll have to wait a bit to show it's characteristic.)

**Part 3**: There is just one conjugacy class of subgroups of each order.

For orders $p$, $q$, and $r$, this follows directly from the Sylow theorems. Let's think therefore about the bigger subgroups whose orders are the product of two primes; without loss of generality let's consider $|H| = pq$, and hence $[G:H] = r$. Where slash how big can $N_G(H)$ be? Because of the normalizer lemma, we know that either $N_G(H) = G$, in which case $|N_G(H)| = pqr$, or $N_G(H) = H$, in which case $|N_G(H)| = pq$.

Now let's apply the orbit-counting theorem

## Pedagogical implications

I think you could build a fun problem sequence out of this, to run alongside a couple weeks of an algebra course. All of the lemmas are pretty accessible 


[^1]: A key part of the D&F argument relies on something that is not true for general $pqr$ (indeed, it's not true for 42). It took me an embarassingly long time to disentangle this.

[^2]: Furthermore, there exist subgroups of order $p^k$ for all $k < n$, and all of them are "nested subgroups" of the Sylow $p$-subgroup(s).