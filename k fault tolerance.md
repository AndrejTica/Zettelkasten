---
date: 2025-10-28
tags:
  - distrubutedsystems
---
When we want to achieve a fault-tolerant system, we define a group of processes that are replicated.
Within that group it can be said that it is k fault tolerant when k number of processes can fail

### How much replication do we need?
- if processes simply stop working, then k + 1 amount of processes. 
- for Byzantine failures, we need 2k + 1 amount of processes. (even if k lie, others form a correct majority)

In real life, we don't know how many k's will fail or be sick, so true fault tolerance is partly statistical based on 
reliability analysis. 
Also to make replication work correctly, all replicas must see the requests in the same order. For this we need to use an [[atomic broadcast]] protocol

