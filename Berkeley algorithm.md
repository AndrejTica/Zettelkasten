---
date: 2025-10-05
tags:
  - distrubutedsystems
---
Is a method of clock synchronization in distributed systems which assumes that no machine has accurate time source. Its intended to be used within intranets.

### Algorithm 
1. A leader is chosen via [[election]] process with for example the [[Chang and Roberts algorithm]].
2. The leader polls the followers who reply with their time in a similar way to [[Christian's algorithm]]
3. The leader observes the roundtrip time of the messages and estimates the time of each follower and its own.
4. The leader then averages the clock times, ignoring any values it receives far outside the value of the others.
5. Instead of sending the updated current time back to the process, the leader then sends out the amount (positive or negative) that each follower must adjust its clock. This avoids further uncertainty due to roundtrip times.

The time daemon must be manually adjusted periodically.

With this algorithm, the individual clock drifting is canceled out. 

Often, any client whose clock differs by too much is disregarded so that it does not influence the average too much. 


### References

