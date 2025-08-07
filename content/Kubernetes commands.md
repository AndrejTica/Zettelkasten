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

When describing a [[Kubernetes Service]] we can view its endpoint
```
kubectl describe service myService
```

Expose the port of a pod (creates a new service)
```
kubectl expose pod <pod> --port=444 --name=frontend
```

Port forward the exposed pod port to the local machine. This is not a proper way of exposing pods, its only for local testing. The real way would be to create a [[Kubernetes Service]].
```
kubectl port-forward <pod> 8080
```

Attach to the pod
```
kubectl attach <podname> -i
```

Add new label to the pod
```
kubectl label pods <pod> mylabel=awesome
```

Run a shell in the pod, useful for debugging.
```
kubectl run -i --tty busybox --image=busybox --restart=Never -- sh
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

## Openshift

Switch projects
```
oc project <project-name>
```

Get projects
```
oc get projects
```

### References

