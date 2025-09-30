---
date: 2025-09-21
tags:
  - distrubutedsystems
  - operatingsystems
---
### Threads vs processes
#### Process:
A process is a single program in execution. Each of these processes gets resources assigned by the operating system in its own isolated address space for the program to run. 
Some of the main OS resources are: 
1. Program space to hold the actual code
2. Data space to hold global and static variables 
3. Registers that hold small amount of data close to the CPU like stack pointer and program counter
4. Heap
5. Stack

Because each of these processes is isolated, when one crashes it does not influence others. 
Even if we have a single core CPU, multiple processes can appear as if they are running at the same time through very fast context switching. 

#### Thread
A thread is a unit of execution within a process. Each thread only have their own Registers and Stack, but the rest of the resources are shared with the process and this makes them more light-weight than processes. 
The problem is that a single thread can corrupt an entire process. 
There are [[User level vs kernel level threads|user level threads and kernel level threads]].



### References

