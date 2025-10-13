---
date: 2025-09-30
tags:
  - distrubutedsystems
  - networking
---
Used to sync multiple clocks, as otherwise it can cause [[Clock synchronization problems|problems]]. 

In praxis we have an NTP server that clients can contact. 
Within, it keeps a score system called "Stratum" from 0 to 15. It tells how accurate the time is by comparing the distance to the reference clock. 0 is the most accurate while 16 is considered unsynchronized. So some NTP servers are "better" than others. Stratum 1 servers are called primary servers as they get their time directly from the reference clocks like an atomic clock. 


There are many online NTP servers that range from Stratum 1-3 NTP servers. If we for example connect to a stratum 2 NTP server, our connecting device becomes a stratum 3 device. 
NTP servers can also "peer", which means connecting multiple servers on the same stratum level to obtain more accurate time. This is called the "symmetric active" mode. 
#### In a nutshell
The client asks the NTP server what time it is, the server responds with a time. 
The client then calculates how long the request/response roundtrip took and adjusts its time accordingly in gradual steps (not at once). 

### More in-depth 
We poll few different time servers in an interval. For each packet, we will calculate the delay and the offset for that server. 
Then we will pass those values to a series of filters until down the end we are left with a single value which will be our best estimate clock offset. That offset is then passed to a "clock discipline algorithm" which then actually adjusts our system clock. 
That then feeds back at the start and forms a feedback loop. 

### Calculating offset and delay
![[Pasted image 20250930170537.png]]

$$
\Large δ = (t_4 - t_1) - (t_3 - t_2)
$$
Offset calculation (the difference between the times, can be negative):

Request: 
$$
	t_1 + \frac{δ}{2} + O = t_2
$$
Response:
$$
	t_3 + \frac{δ}{2} - O = t_4
$$
Solving for offset:
$$
O =	\frac{t_2 - t_4 + t_3 - t_1}{2}  
$$
### References


