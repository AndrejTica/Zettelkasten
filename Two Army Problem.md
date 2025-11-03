---
date: 2025-11-03
tags:
  - distrubutedsystems
---
This is an allegory of two generals that need to communicate a coordinated attack but the messages
travel through enemy territory. The problem asks the question, whether both generals can be certain that they 
will attack at the agreed time.
It turns out, this problem is impossible to solve, as it would require infinite series of ACK messages because any ACK
message may be lost or captured just as the initial message.
The only solution is to increase confidence:

- Send many messages to increase confidence. 
- Add sequence numbers so that the receiver can estimate channel reliability.



