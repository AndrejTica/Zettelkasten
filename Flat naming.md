---
date: 2025-09-29
tags:
  - distrubutedsystems
  - networking
---
Here, the name of the entity does not contain any information where the entity is located. 
Its often used in local area networks where we don't have too many machines.
We can identify the entities with flat names with a broadcasting requester. The requester asks every single machine in the network if they contain an entity with this name identifier, and the one that does responds back. This principle is used in the [[Address resolution protocol (ARP)]]. 
Since broadcasting to every single entity is not scalable, we can use multicast instead. We can allow entities to join a multicast group, and the request are then send to this multicast group. 

We can also use [[Forwarding pointers]].


### References

