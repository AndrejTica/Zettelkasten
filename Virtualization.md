---
date: 2025-09-26
tags:
  - operatingsystems
  - distrubutedsystems
---
In its core, virtualization is just taking one interface, and implementing another interface on top of it.

![[Pasted image 20250926165933.png]]

There are two types of processes.
### Process virtual machine
This means we simply build an interface that runs on a single process that controls the underlying applications. Examples are the JWM, python interpreter. Focus on single processor

### Virtual machine monitor
This one can work with multiple processes as it simulates the entire OS itself and can therefore create multiple virtual machines.
![[Pasted image 20250926171539.png]]
This is also called a hypervisor. There are type 1 and type 2 hypervisors. 

Type 1: Also called bare metal hypervistor. Runs directly on physical hardware with no host os. Examples are Proxmox and VMware ESXi

Type 2. Runs on top of a normal OS. Example is Virtual Box
### References

