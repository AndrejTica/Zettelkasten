---
date: 2025-10-13
tags:
  - distrubutedsystems
---
Two primary reasons for replication: Performance and reliability. 
### Reliability 
- We have 3 copies of a file and every read/write operation is performed on each copy. We can safeguard ourselves against a single failing write operation by considering the value returned by the last two copies as the correct one. 
- If one server fails, others keep running -> increased availability.
### Performance 
When a server is replicated, work can be divided. Often we need a [[load balancer]] in front for that. 
Replication in respect to geographical area can also increase performance as the server may be closer to the client. 

### Problems
Replication can lead to consistency problems. If we update one thing, we need to update other replicas as well.
Example: Web Page. If a webpage is stored by the browser in the cache, we get excellent access time. However if the page updates meanwhile, the user is left with a outdated copy. A solution is to forbit the client of caching, but that leads to poorer performance as the client now might need to do unnecessary calls to the server. 

### References

