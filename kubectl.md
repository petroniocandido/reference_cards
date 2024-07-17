# kubectl Reference Card

## Local configuration

~/.kube/config is the local configuration file (contains all the contexts, information about the clusters and user credentials)

| Command | Description |
| --- | --- |
|```kubectl config current-context``` |  get current context
|```kubectl config get-contexts``` | display context configuration
|```kubectl config use-context <cluster-name>``` | change context
|```kubectl config get-clusters``` | Get cluster name

### Formatting output

| Command | Description |
| --- | --- |
-o=name	| Print only the resource name and nothing else
-o=wide	| Output in the plain-text format with any additional information, and for pods, the node name is included
-o=json	| Output a JSON formatted API object
-o=yaml	| Output a YAML formatted API object

### Other Parameters
| Command | Description |
| --- | --- |
 --field-selector <yaml.file.field>==<value> | In get statement, return only the objects that match with the field
 -l <label-name>==<label-value> | In get statement, return only the objects that have the label

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

## Objects
### Namespaces (ns)

| Command | Description |
| --- | --- |
|```kubectl get namespaces``` | list all namespaces
|```kubectl create ns <name>``` | create a new namespace

### Pods

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
| Command | Description |
| --- | --- |
|```kubectl get secrets -A``` | see all secrets in all namespaces

### CronJobs (cj)

| Command | Description |
| --- | --- |
|```kubectl create cronjob my-cron --image=busybox --schedule="*/5 * * * *" -- echo hello``` | create a CronJob
|```kubectl edit cronjob/my-cron``` | update a CronJob
|```KUBE_EDITOR="nano" kubectl edit cronjob/my-cron``` | update a CronJob with a specific IDE
|```kubectl delete cronjob my-cron``` | delete a CronJob

### ConfigMap

### Deployments

| Command | Description |
| --- | --- |
|```kubectl get deployment``` |

### Services

| Command | Description |
| --- | --- |
|```kubectl get services -A``` | see all services in all namespaces

### Events

| Command | Description |
| --- | --- |
|```kubectl get events --sort-by=.metadata.creationTimestamp```| 

### Ingress

| Command | Description |
| --- | --- |
|```kubectl get ingress -A``` | see all ingresses in all namespaces
|```kubectl get ingress mymicroservice -o yaml``` | see a resource definition

## Actions
### Scale
| Command | Description |
| --- | --- |
|```kubectl scale deployments/<container-name> --replicas=<expected-number-of-replicas> ``` |  to scale the deployment to expected number of replicas

### Port forwarding
| Command | Description |
| --- | --- |
|```kubectl port-forward xxx 8080:80``` |
|```kubectl expose --port=<port-number> --target-port=<port-number <container-name> ``` | Expose a resource as a new Kubernetes service.

### Proxy
| Command | Description |
| --- | --- |
|```kubectl proxy```|  runs a proxy to the Kubernetes API Server

