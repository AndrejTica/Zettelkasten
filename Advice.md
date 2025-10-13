---
date: 2025-03-05
tags:
  - spring
  - architecture
---
In [[Aspect|ascpect]] and functional programming, advice describes a class of functions that modify other functions when the latter are run. Those get executed at a given [[JoinPoint|join point]] of a programm. Those join points can be method calls, field access or exceptions.


### Use
Generally to modify or extend the behavior of functions which cannot or should not be. Its similar to python decorators or java annotations, but advices don't require the actuall modification of the class that the method is in.
Careful: advices can introduce confusion as its not apparent from the method that gets modified, that its getting modified externally. 

### References

