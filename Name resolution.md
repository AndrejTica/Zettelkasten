---
date: 2025-09-28
tags:
  - distrubutedsystems
  - networking
---
Since we can't have a single server that holds the name to address bindings, we must distribute the work across many computers. 

So the names are decomposed into several parts, and the lookup happens recursively. For example:
ftp.cs.vu.nl.
The first server that is responsible for all server that resolve "nl" will look in its lookup table which server is responsible to resolve all servers that end with "vu.nl". This continues until we reach the so called root server that holds the actual mapping of the address. 

There are multiple ways in which we can do name resolution:
1. [[Flat naming]]


### References

