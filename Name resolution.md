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
1. [Flat naming](#flat-naming)
2. [Forwarding pointers](#forwarding-pointers)
3. [Hierarchical location schemes](#hierarchical-location-schemes)

## Flat naming

Here, the name of the entity does not contain any information where the entity is located. 
Its often used in local area networks where we don't have too many machines.
We can identify the entities with flat names with a broadcasting requester. The requester asks every single machine in the network if they contain an entity with this name identifier, and the one that does responds back. This principle is used in the [Address resolution protocol (ARP)](Address%20resolution%20protocol%20%28ARP%29.md). 
Since broadcasting to every single entity is not scalable, we can use multicast instead. We can allow entities to join a multicast group, and the request are then send to this multicast group. 

We can also use [Forwarding pointers](#forwarding-pointers).

## Forwarding pointers

When an entity moves from computer A to computer B in a network, how can we let the callers know where to find the new location without updating the DNS server?
We can leave behind a trail of notes. It tells anyone who calls A: "Hey, im not at location B". This process continues every time the location changes. 

### Pros
- Simple, we don't need to update the DNS server.

### Cons
- If anywhere in the chain the link breaks we are lost. 
- May need a long sequence of hops which is inefficient.

## Hierarchical location schemes

In hierarchical location schemes, a network is divided into a collection of domains. There is a single top-level domain that spans the entire network. Each domain can be divided into smaller sub-domains. 
The smallest level domain is called leaf-domain and it typically is a local area network.
Each domain has a node directory that contains the entries of all entities within that domain. This leads to a tree of directory nodes.
