---
date: 2025-03-10
tags:
  - docker
  - kubernetes
---
Login into the openshift cluster
```
oc login "url" --token="token"
```

List all pods in the current namespace
```
kubectl get pods
```

Get details about a pod
```
kubectl describe pod <pod-name>
```

Get logs from a container, if a container has multiple containers, specify the container using the "--c container-name" flag.
```
kubectl logs <pod-name>
```

Execute a command from within a container of a pod.
```
kubectl exec pod-name --command
```

Apply a config file to create or update resources declaratively. This is the recommended way to provision kubernetes resources.
```
kubectl apply -f config.yaml
```

Delete a resource defined in the yaml file or straight by using the pod itself.
```
kubectl delete pod pod-name
kubectl delete -f config.yaml
```

Adjust the number of replicas in a deployment. 
```
kubectl scale --replicas=10 deployment/deployment-name
```



### References

