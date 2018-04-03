# kubernetes-command
Important Kubernetes command 
## Version of Kubectl
```kubectl version```

## Cluster information 
```kubectl cluster-info```
## Bash Completion (Optional)
```source <(kubectl completion bash)```
## Running single instance of nginx 
``` kubectl run nginx --image=nginx:1.10.0```

In Kubernetes, all containers run in pods. And in this command, Kubernetes created what is called a deployment behind the scenes, and runs a single pod with the nginx container in it. A deployment keeps a given number of pods up and running even when the nodes they run on fail. In this case, you run the default number of pods, which is 1.
## Get POD is running or not
```kubectl get pods ```
## Exposing the pods to outside of container 
``` kubectl expose deployment nginx --port 80 --type LoadBalancer ```

Remember we created nginx pod. 
Kubernetes created a service and an external load balancer with a public IP address attached to it (you will learn about services later). The IP address remains the same for the life of the service. Any client who hits that public IP address (for example an end user or another container) is routed to pods behind the service. In this case, that would be the nginx pod.
