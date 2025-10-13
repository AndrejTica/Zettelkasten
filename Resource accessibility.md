---
date: 2025-09-07
tags:
  - distrubutedsystems
---
The main goal of a [[Distributed systems intro|distributed system]] is to make resources easily available to users. This could be anything from websites, printers, files, networks etc. [1, p. 20]
One reason might be economics, as its cheaper to share one printer amongst many users than each user having their own printer. 
Users should successfully be able to interact with the system at any given time. 
A distributed system is said to be accessible if a non-failing client can send a request to a non-failing node and always get a response. 
For example, a distributed system could be alive, but if network firewall is blocking the access to it, then the service is inaccessible from the clients perspective. [2]


### References
[1] A. S. Tanenbaum and M. van Steen, Distributed Systems: Principles and Paradigms, 2nd ed. Upper Saddle River, NJ, USA: Pearson Prentice Hall, 2007.
[2] [2] OpenAI, "ChatGPT (Mar 2025 version)," OpenAI, San Francisco, CA. [Online]. 
