---
date: 2025-10-27
tags:
  - distrubutedsystems
---
One thing is to use algorithms that tolerate faults, another is once failure occurs, its essential to recover into the correct state.
There are two forms of recovery:
### Backwards recovery
The main issue is to bring the system back into its previous correct state. To do so, we need to record system state from time to time.
Example: Resending a lost packet by the sender. 
Most widely used in distributed systems.
Problems: 
- Most of the time a rollback is costly operation in terms performance. 
- Once the rollback (or reboot when cheap) is done, there is no guarantee that the system won't go into the same failure again.
- Sometimes its simply not possible to rollback, like for example when doing the rm command on the root directory recursively.
Rollbacks are often done together with message logging. That means, when a snapshot is taken, the logs after that snapshot get carried over to the
rolled back snapshot, this way we can more easily debug what went wrong. 

### Forward recovery
Here, instead moving back to a previous state, we move forward by trying to bring the system into a valid new state before continuing.
Main problem with this is that it needs to know in advance which failures might occur. Only then its possible to correct the errors by moving
into a new state.
Example: Erasure correction, this means that the missing packet can be reconstructed from other packets that arrived.

### Storage of checkpoints
We need to store snapshots so that it survives crashes and most hardware failures, this is called stable storage.
Types
- RAM: lost on power out or failure
- Disk: Survives CPU crashes but can fail itself. 
- Stable storage: designed to survive almost everything except stuff like earthquakes or meteor strikes.
How stable storage is implemented:
Use two mirrored disks. On recovery compare disks block by block and if they differ trust disk 1 (it was always updated first).
and copy its block to disk 2. 


