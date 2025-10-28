---
date: 2025-10-27
tags:
  - "#math"
---
Every number can be written in only one way as a product of primes (Primfaktoren), for example:

$$
60 = 2 \times 2 \times 3 \times 5
$$
But 1 is not considered a prime, because then we would loose this fundamental property:

$$
60 = 2 \times 2 \times 3 \times 5 \times 1
$$

$$
60 = 2 \times 2 \times 3 \times 5 \times 1 \times 1
$$
## The list of primes goes on forever. Proof:
There is no rule to determine the next prime from a prime.
Euclid in his book "The elements" came up with a different approach:

Lets assume that there are not infinite:
$$
p_1,p_2,p_3...p_n 
$$
Now construct a new number by multiplying all primes together and adding one:
$$
N = (p_1 \times p_2 \times p_3 \times ... p_n) + 1
$$
Now observe that when you divide N by any of the known primes, there is always a remainder of 1:
$$
N \space mod \space p_i = 1 
$$
Two possibilities:
1. N itself is prime -> new prime we didn't know about
2. N is composite -> not prime but is composed of new primes 

Therefore, there are infinitely many prime numbers.

## Generalization 
Using [[Congruence]] and Euclids proof we can also proof that there are infinitely many primes in the form 4n + 3 or 4n + 1 but not 4n + 2 because every number here is divisible by 2.

This is related to [[Dirichlet's theorem]]

### Fun facts:
- There are infinitely many primes ending with 9, 1, 3 and 7.
- There are special primes called [[Mersenne primes]]



### References

