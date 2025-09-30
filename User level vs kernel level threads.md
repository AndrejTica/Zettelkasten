---
date: 2025-09-21
tags:
  - operatingsystems
---
The difference lies in where the threads are managed and the resulting trade offs. 

### User level threads
Managed by the user-space library. The kernel only knows about the process and not about the threads within. 
- Thread control (creation, scheduling, synchronization) is done at runtime library 
- Creating and context switching have lower overhead since no [[syscalls]] have to be made.
- Portable as they can run on different OS's. 
- Drawback: If one thread makes a I/O blocking call, the whole process blocks as the OS does not know about other threads. 

### Kernel level threads
- Managed by the OS
- Thread control requires syscalls. (more overhead)
- Parallelism. The kernel can schedule multiple threads on different cores.
- Blocking calls dont block the entire process, since kernel can run another thread from the same process

### Hybrid: lightweight processes (LWP)
#todo 





### References

