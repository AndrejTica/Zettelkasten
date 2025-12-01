---
date: 2025-10-27
tags:
  - distrubutedsystems
---
Goal is to achieve multiple transactions to be executed at the same time, but in such a way that it leaves
no data in invalid state. The whole idea is to properly schedule conflicting transactions. Transactions are conflicting if they
operate on the same data and if at least one of them is a read operation.
This is achieved by giving access to data in a specific order, so that when done the final state is as if 
all transactions have been ran sequentially. 

## 3 managers
Concurrency control is best understood with 3 layered managers. 
### Data manager
Bottom layer is the data manager. It performs the actual read and write operations. It's not concerned about which 
transaction is performing the read/write. It knows nothing about transactions.
### Scheduler
Middle layer is the scheduler and carries the main responsibility of controlling the concurrency. It controls which
transactions are allowed to pass read/write operations to the data manager and at which time. It does so that it ensures
that read/write operations are isolated and consistent. Scheduling can be achieved with locks or timestamps.
### Transaction manager
The highest layer and is responsible to guarantee the atomicity of each transaction. It processes the transaction primitives by 
transforming them into scheduling request to the scheduler. 

So what algorithms can we use to achieve this goal of each transaction being isolated and the result same as if executed at the same time?
There are two ways in which we can approach this. Pessimistic and optimistic. 
- Pessimistic: Murphy's law -> if something can go wrong, it will. Here, operations are synced before executed, meaning that conflicts are resolved before they
can happen.
Optimistic: In general nothing will go wrong. Syncing takes place at the end of the transaction. If there conflicts occur, one or more 
transactions are forced to abort.


