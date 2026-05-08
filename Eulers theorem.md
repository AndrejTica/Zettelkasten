---
date: 2025-10-28
tags:
  - "#math"
---
Eulers theorem is a useful tool to:
1. Solve congruences with large exponents
2. Next to [Euclidean Algorithm](/Euclidean%20algorithm.md) its is also a way to calculate the
   multiplicative inverse.

$$
a^{\varphi(m)} \equiv 1 \pmod{m}
\quad \text{if } \gcd(a,m)=1
$$

The Phi symbol stands for [Eulers Phi function](/Eulers%20phi%20function.md).

## Example how we can solve a congruence using Eulers theorem:

$$
7^{321} \ mod \ 8
$$

First step is to calculate the Phi function which is in this case 4.

So then automatically we know that:

$$
7^4 \equiv 1 \ mod \ 8
$$

Now we try to bring this into our original equation. First step is to break up
the exponent like so:

$$
7^{4*80 } * 7 \equiv 7^{321}
$$

which is same as:
$$
(7^{4})^{80} * 7 \equiv 7^{321}
$$

Then we can insert this into our eulers expression, but remember:
In eulers theorem, if we again raise the left side by something, the
expression still holds true because on the other side raising it means
raising 1 to something which is still one.

$$
    1^{80} = 1    
$$

So:


$$
1^{80} * 7 \equiv 1 * 7 \ mod \ 8 
$$

So we end up with:

$$
7 \equiv 7 \ mod \ 8
$$

So the solution is 7.

## Calculating multiplicative inverse

The definition of multiplicative inverse:

$$
a * x \equiv 1 \ mod \ m
$$

If we split away one base from the Eulers theorem we get:

$$
a * a^{\varphi(m) - 1} \equiv 1 \ mod \ m
$$

So that means if we calculate:

$$
a ^{-1} = a^{\varphi(m) - 1}   
$$

## Special case: Fermat Little Theorem
A special case of Eulers theorem is Fermat's little theorem.
If is just the case when m is prime. In that case, the [Phi
function](/Eulers%20phi%20function.md) result becomes m - 1, and therefore:

$$
a^{m-1} \equiv 1 \ mod \ m
$$

or:

$$
a^{m} \equiv a \ mod \ m
$$

To get the multiplicative inverse with Fermats Little Theorem, its with:

$$
a^{-1} \equiv a^{m-2} \ mod \ m
$$

Prime moduli are extremely important in number theory, thats why this formula is
important. 
