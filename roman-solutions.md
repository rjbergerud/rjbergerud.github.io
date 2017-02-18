---
title: Solutions to Steve Roman's Linear Algebra, GTM series
category: math
---

### Chapter 1 Exercises

* **1) Let $$V$$, be a vector space over $$F$$.  (a) Prove that $$0v = 0$$ and (b) $$r0 = 0$$ for all $$v \in V$$ and $$r \in F$$.  Describe the different $$0$$'s in these equations.  (c) Prove that if $$rv = 0$$, then $$r = 0$$ or $$v = 0$$.  (d) Prove that $$rv = v$$ implies that $$v = 0$$ or $$r = 1$$.**

Proof: (a) To prove $$0v = 0$$, we could show that $$0v$$ acts as the additive identity, and hence by uniqueness of the additive identity will be $$0$$.  
Let $$0v = u$$.  Then

$$u = 0v = (2 \cdot 0)v = 2(0v) = 2u = (1 + 1)u = (1)u + (1)u = u + u$$

I spent a couple of minutes trying to prove $$1(u) = u$$ from the other properties of scalar multiplication before realizing that it was an axiom itself.

Subtracting $$u$$ both sides of the equation gives us the desired result.

(b) $$r0 = 0$$  $$\forall r \in F$$.
Our strategy here will be to show $$r0$$ fulfills the the role of the zero vector.  If we can get the $0$ vector in the vector $$r0$$ on its own, we can let it do its job.

$$ r0 + v = r(0 + (1/r)v) = r((1/r)v) = v $$

(c) $$rv = 0$$.  To prove that one of $$r$$ or $$v$$ must be zero, we assume they are both non-zero and derive a contradiction.

If $$r$$ is non-zero, then we can take its inverse

$$ v = (1/r)rv = (1/r)(0) = 0 $$

The last step justified by part (b)!

(d) $$ rv =v \implies rv -v = 0 \implies rv + (-1)v = (r-1)v = 0$$ implies $$r = 1$$ or $$v = 0$$.

* **2) Prove Theorem 1.3.**  *The set $$S(V)$$ of all subspaces of a vector space $$V$$ is a complete lattice under set inclusion, with smallest element $$\{0\}$$, largest element $$V$$, meet*

$$glb\{S_i | i \in K\} = \bigcap_{i \in K} S_i$$

*and join*

$$lub\{S_i | i \in K \} =  \sum_{i \in K}S_i$$

Proof:

* $$S(V)$$ is a lattice:
Can we find an upper bound for every pair of elements in this poset?  Sure, just take their sum.  For a lower bound, take their intersection.

* $$S(V)$$ is a complete lattice:
Well, we want to find a least upper bound (the join) and a greatest lower bound (the *meet*, like as in the set where all the other sets meet). If we can additionally show that the meet and join of $$S(V)$$ belongs to the poset, then there is a largest and smallest element in the lattice, and it is complete.

Let's start with out candidate for greatest lower bound.  It is definitely a lower bound, since $$\bigcap_{i \in K} S_i \subset S_i$$ for the subsets mentioned in index $$K$$.  But also, we want any vector space $$L$$ that is "less than" (contained in) all vector spaces $$S_i$$ $$i \in K$$ to be contained in this candidate $$gup$$.  As a subset of every $$S_i$$ (or being \*less than\* every $$S_i$$), every element contained in $$L$$ must belong also belong in every $$S_i$$, and hence their intersection.  So $$\bigcap S_i$$ contains every other lower bound, and hence is the greatest lower bound.

Notice there was nothing special in this argument that required vector spaces.  As a set, $$\bigcap S_i$$ is also the lower bound in the powerset of $$V$$.  It just happens to also work as a lower bound in $$S(V)$$ because it is a vector subspace of $$V$$, so also belongs to $$S(V

For the least upper board, the gist is this: $$\sum_{i \in K} S_i$$ clearly contains any $$S_i$$, and so is an upper bound.  If $$U$$ is an upper-bounding subspace, then it must contain all $$S_i$$'s, and hence any finite linear combination of elements thereof, and so contains the sum of all subspaces.


* 4) **Suppose that $$V$$ is a vector space with basis $$\mathcal{B} = \{ b_i : i \in I \}$$ and $$S$$ is a subspace of $$V$$.  Let $$\{B_1, .., B_k\}$$ be a partition of $$\mathcal{B}.$$  Then is it true that**:

$$ S = \oplus^k_{i = 1}(S\cap \langle B_i \rangle)$$

**What if $$S \cap \langle B_i \rangle \neq \{0\}$$ for all $$i$$?**

Answer: No, the statement does not always hold.  Take, in $$R^4$$, the basis

$$\{e_1, e_2, e_3, e_4 \}$$

We want to partition this in such a way that each class intersects a subspace $$S$$, but that between these subspaces, $$S$$ misses out on something that happens between the span of different classes.

Also note, that observing the dimensionality here can help us chase down a counterexample. If we satisfy our constraint, then the dimension of $$S$$ will have to be greater than the number of classes in the partition.

Let $$S = span(e_1, e_2 + e_3, e_4)$$

Then
$$S \cap \langle e_1, e_2 \rangle = \{e_1\}$$
$$S \cap \langle e_3, e_4 \rangle = \{e_4\}$$
but $$S \neq \langle e_1, e_4 \rangle $$
