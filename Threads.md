---
date: 2025-09-21
tags:
  - distrubutedsystems
  - operatingsystems
---
## Threads vs processes
### Process
A process is a single program in execution. Each of these processes gets resources assigned by the operating system in its own isolated address space for the program to run. 
Some of the main OS resources are: 
1. Program space to hold the actual code
2. Data space to hold global and static variables 
3. Registers that hold small amount of data close to the CPU like stack pointer and program counter
4. Heap
5. Stack

Because each of these processes is isolated, when one crashes it does not influence others. 
Even if we have a single core CPU, multiple processes can appear as if they are running at the same time through very fast context switching. 

### Thread
A thread is a unit of execution within a process. Each thread only have their own Registers and Stack, but the rest of the resources are shared with the process and this makes them more light-weight than processes. 
The problem is that a single thread can corrupt an entire process. 
There are [user level threads and kernel level threads](#user-level-vs-kernel-level-threads).

## User level vs kernel level threads

The difference lies in where the threads are managed and the resulting trade offs. 

### User level threads
Managed by the user-space library. The kernel only knows about the process and not about the threads within. 
- Thread control (creation, scheduling, synchronization) is done at runtime library 
- Creating and context switching have lower overhead since no [syscalls](syscalls.md) have to be made.
- Portable as they can run on different OS's. 
- Drawback: If one thread makes a I/O blocking call, the whole process blocks as the OS does not know about other threads. 

### Kernel level threads
- Managed by the OS
- Thread control requires syscalls. (more overhead)
- Parallelism. The kernel can schedule multiple threads on different cores.
- Blocking calls dont block the entire process, since kernel can run another thread from the same process

### Hybrid: lightweight processes (LWP)
#todo
