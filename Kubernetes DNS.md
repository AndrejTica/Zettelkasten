---
date: 2025-04-30
tags:
  - kubernetes
  - devops
---
Has built in DNS server. It automatically creates DNS records for [[Kubernetes Service]] and [[Pod|pods]]. 

By default a clients Pod's DNS search list includes the Pod's own namespace and the clusters default domain. 

## Namespaces and Services

A DNS query may return different results based on namespace of the pod making it. DNS queries that don't specify a namespace are limited to the pod's namespace. Access Services in other namespaces by specifying it in the DNS query.




### References

