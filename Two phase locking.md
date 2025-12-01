---
date: 2025-10-27
tags:
  - distrubutedsystems
  - todo
---
Oldest and most widely used [[Concurrency Control]] algorithm is two phase locking.
Basically, when a process needs to read or write data as part of transaction, it requests the scheduler for a lock for that data item.
Likewise, when the data is no longer needed, the lock is released. The scheduler should lock and release the locks in such a way that
only valid schedules result. One such way is two phase locking and it can be considered a pessimistic approach:
First the scheduler gets all the locks in a growing phase until it hits a "lock point" which is the point where maximum locks have been set, and then releases them all in a shrinking phase. More specifically, the following 
rules apply:




