# Kubernetes Tools and Distributions

- https://collabnix.github.io/kubetools/

## k8s Distributions
- [k0s](https://k0sproject.io/) - Zero Friction Kubernetes. k0s is an all-inclusive Kubernetes distribution, which is configured with all of the features needed to build a Kubernetes cluster and packaged as a single binary for ease of use.
- [k3s](https://k3s.io/) - Lightweight Kubernetes distribution for resource-constrained environments.
- [k8s](https://kubernetes.io/)
- [Minikube](https://minikube.sigs.k8s.io) -
- [Microk8s](https://microk8s.io/)
- [Rancher](https://www.rancher.com/)  - Enterprise Kubernetes Management. It addresses the operational and security challenges of managing multiple Kubernetes clusters, while providing DevOps teams with integrated tools for running containerized workloads.
- [Podman](https://podman.io/)

## CRI - Container Runtime Interface
- [containerd](https://github.com/containerd/containerd)
- [CRI-O](https://cri-o.io/)
- [docker]()

## CNI - Container Network Interface
- [calico](https://github.com/projectcalico/calico):
- [cilium](https://github.com/cilium/cilium)

## CSI - Container Storage Interface
- 

## CRD - Customer Resource Definition
- Enables the extension of the Kubernetes API with user-defined custom objects
- CRDs provide a mechanism to introduce new, custom resource types into a Kubernetes cluster, allowing users to define and manage application-specific data or infrastructure components as first-class Kubernetes objects.
- O CRD é definido por um YAML
- O CR - Custom Resource é um objeto do tipo definido pelo CRD
- https://medium.com/@muppedaanvesh/a-hand-on-guide-to-kubernetes-custom-resource-definitions-crds-with-a-practical-example-%EF%B8%8F-84094861e90b 

## Tools
- [ansible](https://www.ansible.com/) - Architecture as code:  IT automation engine that automates provisioning, configuration management, application deployment, orchestration, and many other IT processes.
- [Helm](): Package manager for Kubernetes applications, simplifying deployment and management.
- [k9s](https://k9scli.io/) - Shell CLI
- Portainer
- [kubeTUI](https://github.com/sarub0b0/kubetui)
- [kustomize](): Configuration management tool for customizing Kubernetes manifests.
- [Prometheus](): Monitoring solution for collecting and analyzing metrics.
- [Grafana](): Data visualization and dashboarding tool, often used with Prometheus.
- [argo](https://argoproj.github.io/): Open source tools for Kubernetes to run workflows, manage clusters, and do GitOps right.
- [flux](https://fluxcd.io/): GitOps family of projects for continuous and progressive delivery solutions for Kubernetes that are open and extensible.

## Plugins
- [MetalLB](https://metallb.io/): MetalLB is a load-balancer implementation for bare metal Kubernetes clusters, using standard routing protocols
- [Volcano](https://volcano.sh/en/): Cloud native batch scheduling system for compute-intensive workloads
- [karpenter](https://karpenter.sh/): automatically launches just the right compute resources to handle your cluster's applications. It is designed to let you take full advantage of the cloud with fast and simple compute provisioning for Kubernetes clusters.
- [external-dns](https://kubernetes-sigs.github.io/external-dns/): ExternalDNS synchronizes exposed Kubernetes Services and Ingresses with DNS providers.
- [cert-manager](https://artifacthub.io/packages/helm/cert-manager/cert-manager):  automate the management and issuance of TLS certificates from various issuing sources. It will ensure certificates are valid and up to date periodically, and attempt to renew certificates at an appropriate time before expiry.
- [velero](https://velero.io/):  open source tool to safely backup and restore, perform disaster recovery, and migrate Kubernetes cluster resources and persistent volumes.
- [HAMi]( https://project-hami.io/docs/): Heterogeneous AI Computing Virtualization Middleware
- [OpenCost](https://opencost.io/): Open source cost monitoring for cloud native environments

## Ingress Controllers 
- [traefik](https://traefik.io/traefik): Ingress Controller
- [NGINX Controller](https://github.com/kubernetes/ingress-nginx): Ingress Controller

## Linux 
- [Talos Linux](https://www.talos.dev/) - A modern OS for Kubernetes.
