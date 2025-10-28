---
date: 2025-09-08
tags:
  - distrubutedsystems
---
The main gist of openness in distributes systems are the usage of well-defined interfaces and protocols. 
Benefits are:
- Extendibility. New services or resources can be added without having to change the existing implementation. Similar as in the [[Open/Closed principle|open closed principle]] in software design. 
- Interoperability. An NFS client on linux can communicate with an NFS server on windows.
- Portability. Applications written for one system can be moved to another without breaking changes.

If the system is not open, we risk vendor-lock in, poor scalability and fragile integrations. 

Examples of open systems: Internet - built on open standards (HTTPS, DNS, TCP/IP). Any vendor can build a webbrowser or web server and it will work well with others. 

Example of closed system: Proprietary file system that can be only used on the vendor software


### References

