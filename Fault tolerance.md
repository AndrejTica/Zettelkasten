---
date: 2025-10-28
tags:
  - distrubutedsystems
---
Fault tolerance means how well can we deal with faults when they happen.

## Dependability
Covers useful requierements for distributed systems:
### Availability 
Means that the system is ready to be used immediately. A highly available system is one that will
work at any time.

### Reliability 
A system that never crashes but is shut down for two weeks has high reliability but only 98% availability.
Availability is defined in terms of instant time, reliability in terms of time, aka can run continuously without 
failure. 

### Safety
Safety means that when a system fails to operate temporarily, nothing catastrophic happens.

### Maintainability
How easy a failed system can be repaired. 

## Failure, error and fault
### fail
A fail means that the system failed to meet its promises. 

### error
An error is something that might lead to a failure. For example when sending some bits across the network, some packets are 
expected to be damaged. 

### fault
The cause of an error. For example a bad transmission medium might be a fault. 

## Fault persistence

### transient faults
Occurs once and then disappears. If the operation is repeated, the fault goes away.

### intermittent fault
Occurs, vanishes and appears again by its own. This could be a loose connector. 

### permanent fault
One that continues to exists until the faulty component is fixed.

## Failure masking

Three main types of redundancy:

### Information redundancy
Extra bits are added to to allow for error detection or correction. Examples are check digits or hamming codes. 

### Time redundancy
An action is performed multiple times in case the first one fails. Helpful with transient faults.

### Physical redundancy
Extra hardware or processes are added so that a system as a whole can tolerate loss or malfunction of some components.
In biology we also have physical redundancy (two eyes, two kidneys etc..). A plane has more engines than it needs to fly.

## k fault tolerance

When we want to achieve a fault-tolerant system, we define a group of processes that are replicated.
Within that group it can be said that it is k fault tolerant when k number of processes can fail

### How much replication do we need?
- if processes simply stop working, then k + 1 amount of processes. 
- for Byzantine failures, we need 2k + 1 amount of processes. (even if k lie, others form a correct majority)

In real life, we don't know how many k's will fail or be sick, so true fault tolerance is partly statistical based on 
reliability analysis. 
Also to make replication work correctly, all replicas must see the requests in the same order. For this we need to use an [atomic broadcast](atomic%20broadcast.md) protocol
