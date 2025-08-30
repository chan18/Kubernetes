Kubernetes Practice

master nodes ( controle plane ) 
worker nodes ( minions ) 

Cloud :  ( kubernetes service ) - cloud provider handls the master node.  

EKS 
GKS 
AKS 


Control Plane 

Desired State :
EG: 3 containers running any point of time, is a typical desired state 


Control Plane flow: 

When a users request a desired state : 

1. User ( desired state ) -> REST API -> database ( ETCD ) 
2. Kube-controller-manger -> Rest API ( controller manager does  keep triggers the API for new updates )
    *  Kube controller manger will have following controllers in it eg; Scheduler controller
3. Worker nodes runs some workloads 
    * Worker nodes uses some sort of run time eg : docker, CIR-0, container-d are the container runtimes.
    * Kubelet responsible for communicating to control plane.
        * If any scheduled containers, kubelet will trigger container run time to run bunch of containers 
    * Kube-proxy responsible for communication inside the cluster.
4. K8’s building blocks 
    * The pod : pod is a smallest unit we can work with in kubernets
        * A POD contains one or more containers.
        * If multiple containers running in a single pod all of them will have same ip address with different ports.they can communicate between each adjacent containers also share storage 
        * We can schedule multiple pods in kuberenetes cluster.

Kubectl 

Generic syntax : 
Kubectl < get , delete , create > < resource type >

List pods: 
Kubectl get pods

List specific pod: 
Kubectl get pod my-pod

Create : 
Kubectl < create, apply > -f ./my-pod-config.yml

Port forwarding:
Kubectl port-forward my-pod 8080:80

Creating pods : 

Kubectl run —generator=run-pod/v1 webapp –image=k8s4devs.azurecr.io/k8sdevs/webapp:v0.2
