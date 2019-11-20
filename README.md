# kubernetes-command
Important Kubernetes command 

## Version of Kubectl
```kubectl version```

## Cluster information 
```kubectl cluster-info```

## Installing Gcloud on MAC
```
wget https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-272.0.0-darwin-x86_64.tar.gz
tar zzvf tar -xzvf google-cloud-sdk-272.0.0-darwin-x86_64.tar.gz
./google-cloud-sdk/install.sh
```

## How to See the current context? 
```kubectl config get-contexts```

Output will look like: 
CURRENT   NAME                                     CLUSTER                                  AUTHINFO                                 NAMESPACE
          firstcluster                             firstcluster                             firstcluster
*         gke_devops-259604_us-central1-a_devops   gke_devops-259604_us-central1-a_devops   gke_devops-259604_us-central1-a_devops
          minikube                                 minikube                                 minikube

* means your current cluster. 

## How to switch context?

```kubectl config use-context minikube```
It will start connecting to localminikube cluster

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

## Service information 

```kubectl get services ```

You'll see an external IP that you can use to test and contact the nginx container remotely.

## Scaling up the number of backend applications(pods)

``` kubectl scale deployment nginx --replicas 3 ```

## Clean up or Delete the deployment/service

``` kubectl delete deployment nginx```

``` kubectl delete service nginx```

## Explanation of the pods
``` kubectl explain pods```

