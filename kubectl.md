# kubectl Reference Card

## Local configuration

~/.kube/config is the local configuration file (contains all the contexts, information about the clusters and user credentials)

| Command | Description |
| --- | --- |
kubectl config current-context |  get current context

# display context configuration
kubectl config get-contexts

# change context
kubectl config use-context <cluster-name>

Cluster information

# display version
kubectl version

# display cluster information
kubectl cluster-info

# display cluster configuration
kubectl config get-clusters

# get health information for the control plane components (the scheduler, the controller manager and etcd)
kubectl get componentstatuses

# list all the nodes in the cluster and report their status and Kubernetes version
kubectl get nodes

# show the CPU and memory capacity of each node, and how much of each is currently in use
kubectl top pods

# view sereval resources at once
kubectl get deploy,rs,po,svc,ep

Management

# create resources from a manifest file
kubectl create -f <filename>

# create or update resources from a manifest file
kubectl update -f <filename>

# delete resources from a manifest file
kubectl delete -f <filename>

Objects
Namespaces (ns)

# list all namespaces
kubectl get namespaces

# create a new namespace
kubectl create ns hello-there

Pods

# list pods of a specific namespace
kubectl get pods --namespace kube-system

# list pods of all namespaces
kubectl get pods -A

# get more information about a pod
kubectl describe pod

# get log information of a specific pod
kubectl logs

# get pod yaml definition
kubectl get pod -o yaml

# watch pods
watch kubectl get pod --all-namespaces

# desribe a pod
kubectl describe pod <pod-name> --namespace <namespace>

# get pod logs
kubectl logs [--tail=20] [--since=1h] <pod-name>

# display metrics about a pod and its containers
kubectl top pod <pod-name> --containers

# execute commands inside a pod (for investigation purpose)
kubectl exec -it <pod-name> -n <namespace> -- /bin/bash

# download or upload files from a container
kubectl cp my-file.txt <namespace>/<pod-name>:my-file.txt
kubectl cp <namespace>/<pod-name>:my-file.txt my-file.txt

ServiceAccounts

# see all service accounts in all namespaces
kubectl get ServiceAccount -A
