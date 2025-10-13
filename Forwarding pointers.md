---
date: 2025-09-29
tags:
  - networking
  - distrubutedsystems
---
When an entity moves from computer A to computer B in a network, how can we let the callers know where to find the new location without updating the DNS server?
We can leave behind a trail of notes. It tells anyone who calls A: "Hey, im not at location B". This process continues every time the location changes. 

### Pros
- Simple, we don't need to update the DNS server.

### Cons
- If anywhere in the chain the link breaks we are lost. 
- May need a long sequence of hops which is inefficient.


### References

