---
date: 2025-09-22
tags:
  - distrubutedsystems
  - operatingsystems
---
### Multithreaded clients 
To establish high degree of [[Transparency]], we need to conceal long interprocess message propagation times. 
For example, when fetching a HTML page, we can fetch the most important stuff for the user first, allow therefore some degree of usability while in the background we are fetching other components at the same time using threads. 

Another technique is when we have replicated servers. A load balancer might forward different requests to the replicas and therefore achieve faster load times as one server is not overloaded. All this is possible only if the client can handle parallel streams of data aka can do threads. 

### Multithreaded servers
Although there are important be
This is where the main use of threads is found. Because the server is constantly being bombarded with requests, we need to have multitheading capabilities. Otherwise, once a requests is send in and we only have one thread, the whole server will get blocked until that request is processed. Until that is done the server is unresponsive. 

There are 3 basic ways in which we can construct a server:


| Model                   | Characteristics                          |
| ----------------------- | ---------------------------------------- |
| Threads<br>             | Parallelism, blocking systemcalls        |
| Single threaded process | No parallelism, blocking systemcalls<br> |
| Finite-State-Machine    | Parallelism, nonblocking systemcalls     |

Here its meant that using threads are are allowed to afford using blocking sys calls as other threads can resume work. 

[[Finite state machine]] is basically how python implements async/await on only one thread.
This works with nonblocking sys calls (they instantly return) and an event loop that checks the state of the operation periodically. 


### References

