# Helm-charts
Helm charts are packages that contain all the information that Kubernetes needs to know for managing a specific application within the cluster.

Start minikube:

minikube start and check:

pegaz@ubuntu:~/mkube/chm1$ kubectl cluster-info

Kubernetes control plane is running at https://192.168.39.49:8443

CoreDNS is running at https://192.168.39.49:8443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

pegaz@ubuntu:~/mkube/chm1$ kubectl get nodes

NAME       STATUS   ROLES                  AGE   VERSION

minikube   Ready    control-plane,master   12h   v1.22.2

Also more info:

pegaz@ubuntu:~/mkube/chm1$ kubectl describe node

Name:               minikube

Roles:              control-plane,master

Labels:             beta.kubernetes.io/arch=amd64

                    beta.kubernetes.io/os=linux
.
.

