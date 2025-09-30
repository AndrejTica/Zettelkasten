---
date: 2025-09-21
tags:
  - distrubutedsystems
---
There are 3 techniques for scaling:
1. Hiding communication latencies. 
2. Distribution 
3. Replication

### Hiding communication latencies
Important to achieve geographical scalability. Basic idea: try to avoid waiting for responses from the server as much as possible. While waiting for the response, the requester can do other useful things. This is called [[asynchronous communication]]. 
Often however the client does not have much better to do than wait. Especially true in interactive apps. In this case, use a fat client that off-loads some business logic and computation onto the client. 

### Distribution 
Basically means splitting a component into smaller parts and distributing those parts across the system. Like for example [[DNS]] works in such a way that not a single server is responsible for name resolution but many.

### Replication
Helps spread the load and increases availability and can hide much of latency problems. 
Caching is a form of replication. Its making a copy of a resource close to the client. However in contrast to replication, caching is something the client needs to take care of. However we need to be careful with replicated resources to not get mismatches and consistency problems. [[Consistency]] can be helped with some global synchronization mechanism. 
Unfortunately, synchronization mechanisms are very hard to implement in scalable way, as electrical signals travel with a limited speed. 


### References

