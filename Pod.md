---
date: 2025-04-29
tags:
  - kubernetes
  - devops
---
A pod contains one or more containers that share the same network IP, hostname and storage volumes.
Pods are managed by higher level objects like [[Deployments|Deployments]], [[ReplicaSets|ReplicaSets]] etc..

Sample file to define a pod:

```
apiVersion: v1
kind: Pod
metadata:
  name: my-app-pod
spec:
  containers:
    - name: web
      image: nginx
    - name: logger
      image: busybox
	  ports:
	  - containerPort: 3000

```

Create pod with kubectl create -f k8s-demo/pod-helloworld.yml


### References

