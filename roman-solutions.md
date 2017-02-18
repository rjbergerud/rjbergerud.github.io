---
title: Solutions to Steve Roman's Linear Algebra, GTM series
category: math
---

### Chapter 1
Exercises

1.Let $$V$$, be a vector space over $$F$$.  (a) Prove that $$0v = 0$$ and (b) $$r0 = 0$$ for all $$v \in V$$ and $$r \in F$$.  Describe the different $$0$$'s in these equations.  (c) Prove that if $$rv = 0$$, then $$r = 0$$ or $$v = 0$$.  (d) Prove that $$rv = v$$ implies that $$v = 0$$ or $$r = 1$$.

Proof: (a) To prove $$0v = 0$$, we could show that $$0v$$ acts as the additive identity, and hence by uniqueness of the additive identity will be $$0$$.  
Let $$0v = u$$.  Then

$$u = 0v = (2 \cdot 0)v = 2(0v) = 2u = (1 + 1)u = (1)u + (1)u = u + u$$

I spent a couple of minutes trying to prove $$1(u) = u$$ from the other properties of scalar multiplication before realizing that it was an axiom itself.

Subtracting $$u$$ both sides of the equation gives us the desired result.

(b) $$r0 = 0$$  $$\forall r \in F$$.
Our strategy here will be to show $$r0$$ fulfills the the role of the zero vector.  If we can get the $0$ vector in the vector $$r0$$ on its own, we can let it do its job.

$$ r0 + v = r(0 + (1/r)v) = r((1/r)v) = v $$
