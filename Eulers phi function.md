---
date: 2025-10-28
tags:
  - "#math"
---
The amount of numbers in Zm that are coprime to m. If Zm is Z6:

Z6 = 0,1,2,3,4,5

ggT = (0, 6) = 6

ggT = (1, 6) = 1  -> coprime

ggT = (2, 6) = 2

ggT = (3, 6) = 3

ggT = (4, 6) = 2

ggT = (5, 6) = 1  -> coprime


Phi(6) = 2  

However there is formula to calculate it much faster:

Example: Phi(240)

First, get the prime factors of this number: 

$$
2^4, 3^1, 5^1
$$

Then do the following:

$$
Phi(240) = (2^4 - 2^3)(3^1 - 3^0)(5^1 - 5^0) = 64
$$

So just subtract one to the exponent of each prime factor and subtract that from
the original. Repeat for each prime factor and then multiple the results. 

