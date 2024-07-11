# kubectl Reference Card

## Local configuration

~/.kube/config is the local configuration file (contains all the contexts, information about the clusters and user credentials)

| Command | Description |
| --- | --- |
|```kubectl config current-context``` |  get current context
|```kubectl config get-contexts``` | display context configuration
|```kubectl config use-context <cluster-name>``` | change context

## Cluster information

| Command | Description |
| --- | --- |
|```kubectl version``` | display version
|```kubectl cluster-info``` | display cluster information
|```kubectl config get-clusters``` | display cluster configuration
|```kubectl get componentstatuses``` | get health information for the control plane components (the scheduler, the controller manager and etcd)
|```kubectl get nodes``` | list all the nodes in the cluster and report their status and Kubernetes version
|```kubectl top pods``` | show the CPU and memory capacity of each node, and how much of each is currently in use
|```kubectl get deploy,rs,po,svc,ep``` | view several resources at once

## Management

| Command | Description |
| --- | --- |
|```kubectl create -f <filename>``` | create resources from a manifest file
|```kubectl update -f <filename>``` | create or update resources from a manifest file
|```kubectl delete -f <filename>``` | delete resources from a manifest file

## Objects
### Namespaces (ns)

| Command | Description |
| --- | --- |
|```kubectl get namespaces``` | list all namespaces
|```kubectl create ns <name>``` | create a new namespace

### Pods

| Command | Description |
| --- | --- |
|```kubectl get pods -n <namespace>``` | list pods of a specific namespace
|```kubectl get pods -A``` | list pods of all namespaces
|```kubectl describe pod``` | get more information about a pod
|```kubectl logs``` | get log information of a specific pod
|```kubectl get pod -o yaml``` | get pod yaml definition
|```watch kubectl get pod --all-namespaces``` | watch pods
|```kubectl describe pod <pod-name> --namespace <namespace>``` |  desribe a pod
|```kubectl logs [--tail=20] [--since=1h] <pod-name>``` | get pod logs
|```kubectl top pod <pod-name> --containers``` |  display metrics about a pod and its containers
|```kubectl exec -it <pod-name> -n <namespace> -- /bin/bash``` | execute commands inside a pod (for investigation purpose)
|```kubectl cp my-file.txt <namespace>/<pod-name>:my-file.txt``` |  download or upload files from a container
|```kubectl cp <namespace>/<pod-name>:my-file.txt my-file.txt``` |  download or upload files from a container

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
|```kubectl scale``` | 

### Port forwarding
| Command | Description |
| --- | --- |
|```kubectl port-forward xxx 8080:80``` |

### Proxy
| Command | Description |
| --- | --- |
|```kubectl proxy```|  runs a proxy to the Kubernetes API Server
