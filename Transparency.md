---
date: 2025-09-07
tags:
  - distrubutedsystems
---
Important goal of distributed systems is to hide the fact that processes and resources are physically distributed across multiple computers. 
When a distributed system can present itself to users and applications as if it were a single computer system, then its said to be transparent.

### Types of transparency

#### Access - Hide differences in data representation and how resource is accessed. 
How resources can be accessed by users and how data is represented between systems. For example, different hardware might have different machine architectures. We wish to hide the differences, but a more important aspect is to reach an agreement on how data is represented by different operating systems. For example, when using a programming language, the developers should not care whether a file is located on windows or linux and be able to get a handle to the file through the same method.
#### Location - Hide where a resource is located 
The users should not be able to tell if a file is located locally or on a remote machine. 
For example a standard internet URL gives no clue about where actually the website is hosted.
#### Migration - Hide that a resource may move to another location
Resources can be migrated without affecting how they are accessed.
#### Relocation - Hide that a resource may be moved to another location while in use
Stronger case of migration transparency. If we can relocate a resource while running without users noticing anything. Then we can say that the system supports relocation transparency. 
#### Replication - Hide that a resource is replicated  
Hides the fact that several of the same resources exists. Mostly to increase availability or improve performance. A system that supports replication transparency should also support location transparency otherwise we cant refer to the replicas. 

#### Concurrency - Hide that a resource may be shared by several competitive users.**** 
When two users are accessing the same resource, they should not notice it. Like for example accessing the same file on a server or shared database table. We just need to make sure that when its a write operation we use locking **mechanisms** to not cause problems in the transactions. 
#### Failure - Hide the failure and recovery of a resource 
When one resource fails, the user should not notice it. Masking failures is especially difficult in distributed systems. One of the main problems is distinguishing between a dead resource and painfully slow one. 

## Tradeoffs 
Transparency is generally a good thing, but has its tradeoffs:
- Performance. Like replication of a resource takes extra performance to sync the data.
- Increases Complexity
- Counter productive. Like with handheld devices that people carry around, we often need location awareness and don't want to hide it.
- The price to achieve high transparency may be high.

### References

