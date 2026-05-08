---
date: 2025-10-28
tags:
  - "#math"
---
With Euclidean algorithm we can calculate the ggT easily: 

Given two numbers, where r0 is the larger number: 
$$
ggT(r_0, r_1) 
$$

First step of the euclidian algorithm is to reduce this to:

$$
ggT(r_1, r_0 mod r_1)
$$

And just keep repeating this step. Example:

ggt(973, 301) = ggt(301, 70)
ggt(70, 21) = ggt(21, 7)
ggt(7, 0)

When we reach a 0, then the ggT is the second number of the previous
calculation, in this example the 7

## Extended Euclidean algorithm 
With the extended Euclidean algorithm, we can get two additional parameters:

$$
ggt(r_0, r_1) = S * r_0 + t * r_1
$$

And here, the t is the inverse r1, meaning: 
$$
t=r^{-1}
$$

Basically, while going along normally with the algorithm, we do a extra step
in-between  by always 


Example:

ggt(973, 301) 
we do the first iteration and write it as such:

973 = 3*301 + 70  ->  70 = (1)973 + (-3)301

Next iteration:

301 = 4*70 + 21 ->  21 = 301 - 4*70 

Now, we always want to have the form of x*973 + y301, but here the 70 is not
complying with that form, so we have to insert the equation from the first
iteration into the equation of the second iteration: 

21 = 1(301) - 4(973 - 3*301) = (-4)*973 + 13*301

Next iteration:

70 = 3*21 + 7 -> 7 = 70 - 3*21

Now again none of those two parts is our wanted form, so we replace the 21 with
the equation from one iteration above and the 70 from the iteration two times
above:

7 = 973 - 3*301 - (-3)(-4*973 + 13*301) 
7 = 973 - 3*301 + 12*973 - 39*301
7 = 13*973 - 42*301 

### Usage
We can use the EEA to find the multiplicative inverse of a mod m, when a and m
are coprime to eachother, meaning the ggT is 1. 
In that case, the second coefficient of our equation we get at the end is the 
multiplicative inverse of a. 

