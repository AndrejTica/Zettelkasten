---
date: 2025-11-03
tags:
  - distrubutedsystems
---
To get a better grasp of how serious failures are, several models have been developed. 

#### crash failure
A server halts, but is working correctly until the moment it halts. Often reboots are needed in case of operating system halt.
If a server crashes in such a way that it can be detected by other servers, its called fail-stop failures. The opposite of that 
is called fail-silent systems. 

#### omission failure
- receive omission: A server fails to receive messages. 
- send omission: A server fails to send messages. 

#### timing failure. 
Servers response lies outside of its specified time interval. 


#### response failure
- value failure: The value of the response is wrong.
- state transition failure: The server deviates from the correct flow of control.

#### arbitrary failure (Byzantine failure)
- Most severe type, the server behaves unpredictably or maliciously.
- It may send random or false results that appear valid.
- May present different symptoms to different observers. 
- Needs consensus amongst multiple components
- The Byzantine allegory considers a number of generals who are attacking a fortress. 
The generals must decide as a group whether to attack or retreat; some may prefer to attack, while others prefer to retreat. 
The important thing is that all generals agree on a common decision, for a half-hearted attack by a few generals would become a rout, 
and would be worse than either a coordinated attack or a coordinated retreat.

Here, we often need an agreement how to proceed within the processes. We can do this if we make the assumption that [[k fault tolerance]] is 
2k + 1. 

