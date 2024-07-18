# kubectl Reference Card

## Local configuration

~/.kube/config is the local configuration file (contains all the contexts, information about the clusters and user credentials)

| Command | Description |
| --- | --- |
|```kubectl config current-context``` |  get current context
|```kubectl config get-contexts``` | display context configuration
|```kubectl config use-context <cluster-name>``` | change context
|```kubectl config get-clusters``` | Get cluster name

## General Parameters

| Command | Description |
| --- | --- |
|```-o=name```	| Print only the resource name and nothing else
|```-o=wide```	| Output in the plain-text format with any additional information, and for pods, the node name is included
|```-o=json```	| Output a JSON formatted API object
|```-o=yaml```	| Output a YAML formatted API object
|``` --field-selector <yaml.file.field>==<value>``` | In get statement, return only the objects that match with the field
|``` -l <label-name>==<label-value>``` | In get statement, return only the objects that have the label
|``` --all-namespaces, -A``` |  list all kubernetes resources in all namespaces

## Cluster 

### General information

| Command | Description |
| --- | --- |
|```kubectl version``` | display version
|```kubectl cluster-info``` | display cluster information
|```kubectl config get-clusters``` | display cluster configuration
|```kubectl get componentstatuses``` | get health information for the control plane components (the scheduler, the controller manager and etcd)
|```kubectl get nodes``` | list all the nodes in the cluster and report their status and Kubernetes version
|```kubectl top pods``` | show the CPU and memory capacity of each node, and how much of each is currently in use
|```kubectl get deploy,rs,po,svc,ep``` | view several resources at once

### Nodes

| Command | Description |
| --- | --- |
|```kubectl get nodes``` | list all the nodes in the cluster and report their status and Kubernetes version
|```kubectl cordon my-node``` | Mark my-node as unschedulable
|```kubectl uncordon my-node``` | Mark my-node as schedulable
|```kubectl drain my-node``` | Drain my-node in preparation for maintenance
|```kubectl top node``` | Show metrics for all nodes
|```kubectl top node my-node``` | Show metrics for a given node

## Management

| Command | Description |
| --- | --- |
|```kubectl create -f <filename>``` | create resources from a manifest file
|```kubectl create <object-type> [<sub-type>] <instance-name>``` | 
|```kubectl update -f <filename>``` | create or update resources from a manifest file
|```kubectl replace -f <filename|url>``` | 
|```kubectl delete -f <filename>``` | delete resources from a manifest file
|```kubectl edit``` |  Directly edit the raw configuration of a live object by opening its configuration in an editor.
|```kubectl apply -f <filename>``` | 
|```kubectl diff -f <filename>``` | 
|```kubectl patch ``` | Directly modify specific fields of a live object by using a patch string. 
|```kubectl set``` | Set an aspect of an object.
|```kubectl explain pods``` |

## Objects
### Namespaces (ns)

| Command | Description |
| --- | --- |
|```kubectl get namespaces``` | list all namespaces
|```kubectl create ns <name>``` | create a new namespace

## Workloads
- *Pod*: is a group of one or more containers, with shared storage and network resources, and a specification for how to run the containers. Pods are the smallest deployable units of computing that you can create and manage in Kubernetes.
- *Deployment*: provides declarative updates for Pods and ReplicaSets. You describe a desired state in a Deployment, and the Deployment Controller changes the actual state to the desired state at a controlled rate.
- *ReplicaSet*: maintain a stable set of replica Pods running at any given time. As such, it is often used to guarantee the availability of a specified number of identical Pods.
- *StatefulSets*:  manage stateful applications. Manages the deployment and scaling of a set of Pods, and provides guarantees about the ordering and uniqueness of these Pods. Like a Deployment, a StatefulSet manages Pods that are based on an identical container spec. Unlike a Deployment, a StatefulSet maintains a sticky identity for each of its Pods. These pods are created from the same spec, but are not interchangeable: each has a persistent identifier that it maintains across any rescheduling.
- *DaemonSet*:  ensures that all (or some) Nodes run a copy of a Pod. As nodes are added to the cluster, Pods are added to them. 
- *Jobs*:  creates one or more Pods and will continue to retry execution of the Pods until a specified number of them successfully terminate. As pods successfully complete, the Job tracks the successful completions.
- *CronJob*:  creates Jobs on a repeating schedule. One CronJob object is like one line of a crontab (cron table) file on a Unix system. It runs a Job periodically on a given schedule, written in Cron format.
- *ReplicationController*: ensures that a specified number of pod replicas are running at any one time. In other words, a ReplicationController makes sure that a pod or a homogeneous set of pods is always up and available.


| Command | Description |
| --- | --- |
|```kubectl run -i --tty --attach <pod-name> --image <docker-image> -- <command>```| Create a new pod based on a given image and run a command
|```kubectl get pods -n <namespace>``` | list pods of a specific namespace
|```kubectl get pods -A``` | list pods of all namespaces
|```kubectl describe pod``` | get more information about a pod
|```kubectl logs``` | get log information of a specific pod
|```kubectl get pod -o yaml``` | get pod yaml definition
|```watch kubectl get pod --all-namespaces``` | watch pods
|```kubectl describe pod <pod-name> --namespace <namespace>``` |  desribe a pod
|```kubectl logs [--tail=20] [--since=1h] <pod-name>``` | get pod logs
|```kubectl top pod <pod-name> --containers``` |  display metrics about a pod and its containers
|```kubectl exec -it <pod-name> -n <namespace> -- <command>``` | execute commands inside a pod (for investigation purpose)
|```kubectl cp <file-src> <namespace>/<pod-name>:<file-dst>``` |  download or upload files from a container
|```kubectl cp <namespace>/<pod-name>:<file-src> <file-dst>``` |  download or upload files from a container

### ServiceAccounts

| Command | Description |
| --- | --- |
|```kubectl get ServiceAccount -A``` | see all service accounts in all namespaces

### Secrets
- A Secret object stores sensitive data such as credentials used by Pods to access services. For example, you might need a Secret to store the username and password needed to access a database.
  
| Command | Description |
| --- | --- |
|```kubectl get secrets -A``` | see all secrets in all namespaces
|```kubectl describe secret <name> ``` |
|```kubectl create secret generic <name> --from-literal=<key1>=<value1> --from-literal=<key2>=<value2>``` | reate the Secret by passing the raw data 
|```kubectl create secret generic <name> --from-file=<key1>=./file1.txt -from-file=<key2>=./file2.txt``` | reate the Secret by passing files 
|```kubectl edit secrets <name>``` |
|```kubectl delete secret <name>``` |

### CronJobs (cj)

| Command | Description |
| --- | --- |
|```kubectl create cronjob my-cron --image=busybox --schedule="*/5 * * * *" -- echo hello``` | create a CronJob
|```kubectl edit cronjob/my-cron``` | update a CronJob
|```KUBE_EDITOR="nano" kubectl edit cronjob/my-cron``` | update a CronJob with a specific IDE
|```kubectl delete cronjob my-cron``` | delete a CronJob

### ConfigMap
- A ConfigMap is an object used to store non-confidential data in key-value pairs. Pods can consume ConfigMaps as environment variables, command-line arguments, or as configuration files in a volume. ConfigMaps allows you to decouple environment-specific configuration from your container images, so that your applications are easily portable.

### Deployments

| Command | Description |
| --- | --- |
|```kubectl get deployment``` |

### Services, Port-Forwards and Ingress
- *Service*: is a method for exposing a network application that is running as one or more Pods in your cluster. A Service can map any incoming port to a targetPort. By default and for convenience, the targetPort is set to the same value as the port field.
  - *ClusterIP*: Exposes the Service on a cluster-internal IP. Choosing this value makes the Service only reachable from within the cluster. You can expose the Service to the public internet using an Ingress 
  - *NodePort*: Exposes the Service on each Node's IP at a static port
  - *LoadBalancer*: Exposes the Service externally using an external load balancer. Kubernetes does not directly offer a load balancing component; you must provide one
  - *ExternalName*: Maps the Service to the contents of the externalName field (for example, to the hostname api.foo.bar.example). The mapping configures your cluster's DNS server to return a CNAME record with that external hostname value. No proxying of any kind is set up.
- *Ingress*:  Ingress exposes HTTP and HTTPS routes from outside the cluster to services within the cluster. Traffic routing is controlled by rules defined on the Ingress resource. Ingress may provide load balancing, SSL termination and name-based virtual hosting.

- 
| Command | Description |
| --- | --- |
|```kubectl get services -A``` | see all services in all namespaces
|```kubectl describe svc``` | list configuration info and events for all services in the default namespace
|```kubectl create svc nodeport nodeport-svc --tcp=8080:80``` | create nodePort type service 'nodeport-svc' in default namespace, exposing port 8080 from the container port 80
|```kubectl expose deploy nginx --name=app-service --port=80 --type=NodePort``` | create a nodePort service 'app-service' from exposing deployment 'nginx'
|```kubectl expose deploy nginx --port 80 --target-port 80 --type LoadBalancer``` | create a load balancer type service named 'nginx' from a deployment
|```kubectl expose svc nginx --name nginx-https --port 443 --target-port 8443``` | Create a second service based on the above service, exposing the container port 8443 as port 443 with the name "nginx-https"
|```kubectl create ingress cool-ing --rule="mycoolwebapp.com/forums=forums-svc:8080,tls=my-cert"``` | Create an ingress named 'cool-ing' that takes requests to mycoolwebapp.com/forums to our service named forums-svc on port 8080 with a tls secret "my-cert"
|```kubectl create ingress one-ing --rule="/path=myweb-svc:80"``` | Create an ingress named 'one-ing' that takes all requests to a service named 'myweb-svc' on port 80
|```kubectl port-forward xxx 8080:80``` |
|```kubectl expose --port=<port-number> --target-port=<port-number <container-name> ``` | Expose a resource as a new Kubernetes service.



### Events

| Command | Description |
| --- | --- |
|```kubectl get events --sort-by=.metadata.creationTimestamp```| 

### Ingress

| Command | Description |
| --- | --- |
|```kubectl get ingress -A``` | see all ingresses in all namespaces
|```kubectl get ingress mymicroservice -o yaml``` | see a resource definition

### Labels and Annotations
| Command | Description |
| --- | --- |
kubectl label no mynode1 disk=ssd | label node 'mynode1` with key 'disk' and value 'ssd'
kubectl get no --show-labels | show labels for nodes in a cluster
kubectl annotate no mynode1 azure=node | annotate node 'mynode1' with key 'azure', and value 'node'

## Actions
### Scale
| Command | Description |
| --- | --- |
|```kubectl scale deployments/<container-name> --replicas=<expected-number-of-replicas> ``` |  to scale the deployment to expected number of replicas

### Proxy
| Command | Description |
| --- | --- |
|```kubectl proxy```|  runs a proxy to the Kubernetes API Server

## Volumes
| Command | Description |
| --- | --- |
sc | Storage Classe
pv | Persistent Volumes
pvc | Persistent Volume Claims
volumeattachments | view the volumes attached to nodes (non-namespaced)

