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

etc.

Install Helm:

curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get-helm-3 > get_helm.sh

chmod 700 get_helm.sh && ./get_helm.sh

pegaz@ubuntu:~/mkube$ ./get_helm.sh 

Downloading https://get.helm.sh/helm-v3.7.1-linux-amd64.tar.gz

Verifying checksum... Done.

Preparing to install helm into /usr/local/bin

[sudo] password for pegaz: 

helm installed into /usr/local/bin/helm

pegaz@ubuntu:~/mkube$ helm --help
The Kubernetes package manager

Common actions for Helm:

- helm search:    search for charts

- helm pull:      download a chart to your local directory to view

- helm install:   upload the chart to Kubernetes

- helm list:      list releases of charts

etc.





