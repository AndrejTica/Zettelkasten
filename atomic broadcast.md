---
date: 2025-10-28
tags:
  - distrubutedsystems
---
In fault-tolerant distributed computing, an atomic broadcast or total order broadcast is a broadcast where all correct processes in a system of multiple 
processes receive the same set of messages in the same order; that is, the same sequence of messages. 
The broadcast is termed "atomic" because it either eventually completes correctly at all participants, or all participants abort without side effects. 
Atomic broadcasts are an important distributed computing primitive.

The messages are totally ordered in the mathematical sense; that is, if any correct participant receives message 1 first and message 2 second, then every other correct participant must receive message 1 before message 2.

Note that total order is not equivalent to FIFO order, which requires that if a process sent message 1 before it sent message 2, then all participants must receive message 1 before receiving message 2. 
It is also not equivalent to "causal order", where if message 2 "depends on" or "occurs after" message 1 then all participants must receive message 2 after receiving message 1. 
While a strong and useful condition, total order requires only that all participants receive the messages in the same order, but does not place other constraints on that order such as that in which the messages are sent.
