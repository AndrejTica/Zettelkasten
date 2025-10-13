---
date: 2025-09-30
tags:
  - distrubutedsystems
---
### Why is clock synchronization a problem in distributed computing?
If we only have one processor, that means all the processes rely on only one internal clock. This clock may not be accurate, but since its the same clock for all processes, it usually does not cause any problems. However if we have multiple clocks that need to be synched, it can get complicated. Some problems that can arise:
Examples:
- Editing files placed an edited timestamp. Tools like make rely on this an incorrect times can break such tools
- Logs may show up out of order which makes debugging and auditing a pain.
- Security problems as auth tokens have expiration dates.
- Missed deadlines in systems that rely on time. Especially bad in systems like high-frequency trading. 
### Physical clock
The clock inside the computer is a quarz crystal that oscillates under a pretty stable frequency when the crystal is put under tension. Each cycle decrements a counter register, and once the counter reaches 0, an interrupt is triggered that can be picked up by the computer.
For example on cisco IOS we can show the time with the ```show clock``` command that will display the current time in UTC. However it will have an "*" in front of the time, indicating that this time is not authoritative, meaning the device is not sure if the time is correct and hasn't drifted. 

### Problems within multiple physical clocks
When we have multiple processors and therefore multiple physical clocks, over time we get something called clock skew. This is because multiple clocks will drift apart over time due to various natural reasons. 

Thats why its important so sync the clocks with protocols like [[NTP (Network time protocol)]]. 

### References

