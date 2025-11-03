---
date: 2025-10-28
tags:
  - distrubutedsystems
---
## Dependability
Covers useful requierements for distributed systems:
#### Availability 
Means that the system is ready to be used immediately. A highly available system is one that will
work at any time.

#### Reliability 
A system that never crashes but is shut down for two weeks has high reliability but only 98% availability.
Availability is defined in terms of instant time, reliability in terms of time, aka can run continuously without 
failure. 

#### Safety
Safety means that when a system fails to operate temporarily, nothing catastrophic happens.

#### Maintainability
How easy a failed system can be repaired. 

## Fault types
#### fail
A fail means that the system failed to meet its promises. 

#### error
An error is something that might lead to a failure. For example when sending some bits across the network, some packets are 
expected to be damaged. 

#### fault
The cause of an error. For example a bad transmission medium might be a fault. 

## fault types
Fault tolerance means how well can we deal with faults when they happen.

#### permanent faults
meet its promises. 

#### error
An error is something that might lead to a failure. For example when sending some bits across the network, some packets are 
expected to be damaged. 

#### fault
The cause of an error. For example a bad transmission medium might be a fault. 

## fault types
Fault tolerance means how well can we deal with faults when they happen.

#### transient faults
Occurs once and then disappears. If the operation is repeated, the fault goes away.

#### intermittent fault
Occurs, vanishes and appears again by its own. This could be a loose connector. 

#### permanent fault
One that continues to exists until the faulty component is fixed.





### References

