---
date: 2025-03-10
tags:
  - kubernetes
  - docker
---
Enables communication between different microservices. For example our app can have a group of [[Pod|pods]] running various sections like backend or frontend. It is services that enable the connectivity between these group of pods.
We can create a service, tell it to listen to a port on the node that runs the pod, and whatever comes through that port, it remaps it to the pod network. This type of service is known as "Node pod service". We use yaml files to define the service. 

## Service types:
- NodePort
- ClusterIP
- LoadBalancer

### ClusterIP
Good choice if we need internal communication between components but dont need to expose anything to the outside of the cluster. Kubernetes assigns a virtual IP-Address to a clusterip service that can be accessed soley from within the cluster during its creation. 
It is the default service so we dont need to specify the type. 
```
apiVersion: v1
kind: Service
metadata:
  name: backend
spec:
  selector:
    app: backend
  ports:
  - name: http
    port: 80
    targetPort: 8080
```

Here we define a service named backend with a selector that targets pods labeled with app: backend. The service exposes port 80, which is the port used by client to access the service, and forwards the traffic to the pods port 8080, which is where the backend app is running.
### NodePort
Same as ClusterIP but extends the functionality by enabling external connectivity. We can connect to it from outside of the cluster. This is useful when we are on prem and dont have a load balancer provided by the cloud provider. 
There are 3 ports involved here. 
1. TargetPort. For example 80 if we are targeting a http application
2. Port. The port on the service itself. The service is like a virtual server inside the node with its own ip address that is called ClusterIP of the service and therefore needs its own port. 
3. NodePort. The port on the service itself which we use to access the service from outside the cluster. These can only be within the range of 30000-32767. 


### References

