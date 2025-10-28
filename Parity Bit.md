---
date: 2025-10-14
tags:
  - hardware
---
Parity bits are a simple form of error detection. The parity bit ensures that the total number of high bits is either odd or even. Accordingly, there are two variants of parity bits: odd parity bit and even parity bit. 
If we use even parity, the count of bits + parity bit has to be even in count. Reverse is true for odd.

What it detects: Any odd number of bit flips (e.g., 1-bit error) will be caught; an even number of flips can slip through. It detects but does not correct errors.

### References

