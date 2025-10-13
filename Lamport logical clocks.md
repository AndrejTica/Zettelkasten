---
date: 2025-10-05
tags:
  - distrubutedsystems
---
Even if we sync clocks with [[NTP (Network time protocol)]], we can still end up errors in causality by receiving and sending clocks not being the same.
We have seen that it might be sufficient that each node agrees on a time. This time does not need to reflect the actual real time. As seen in the make example, make only needs to know which file is oldest. 
So if we extend this further, often only the order of actions is sufficient. So some algorithms only concern themselves with the correct ordering. For these algorithms, the convention is to speak of logical clocks.

Physical clocks count number of seconds elapsed.
Logical clocks count number of events occurred.

$$
	(e_1 \longrightarrow e_2) \Longrightarrow (T(e_1) < T(e_2))
$$
This is a notation called "happens before" and it says that event e1 should happen before event e2. 
The basic algorithm for this is the Lamport algorithm and it tells us the "partial ordering" of events.
### Partial ordering
Partial ordering means that the chain of causality works only one way, or that we can't detect concurrent events. 
That means with lamport timestamps we can say that:
$$ (e_1 \longrightarrow e_2) $$
But we cannot conclude from it that 
$$ (e_2 \longrightarrow e_1) $$
This is because each node has its own independent clock that can have events in between that the other one does not have. 
By extension we also can't conclude if the events are concurrent or not by looking at their timestamps. 

**Concurrent** in this context means that two events have causal dependency between them, aka the messages have been exchanged between them.
### Lamport logical clocks
Each node has its own logical clock t.

1. On init t = 0
2. Any event that occurs on the local node increment by one.
3. When sending a message to a different node, increment the clock and send this value together with the message to the node. 
4. The receiving node, compares the clock value in the message and its own clock value. It then takes whichever one of those two is higher, and increments it by one, and updates it clock value with this new value. 









### References

