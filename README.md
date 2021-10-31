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

Install an application using a Helm Chart

The steps below show how to run the following Bitnami applications using Helm charts:

helm repo add bitnami https://charts.bitnami.com/bitnami

"bitnami" has been added to your repositories

MongoDB:

pegaz@ubuntu:~/mkube/chm1$ helm install mongodb bitnami/mongodb --set serviceType=NodePort 

NAME: mongodb
LAST DEPLOYED: Sun Oct 31 08:50:40 2021
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
CHART NAME: mongodb
CHART VERSION: 10.28.7
APP VERSION: 4.4.10

** Please be patient while the chart is being deployed **

MongoDB&reg; can be accessed on the following DNS name(s) and ports from within your cluster:

    mongodb.default.svc.cluster.local

To get the root password run:

    export MONGODB_ROOT_PASSWORD=$(kubectl get secret --namespace default mongodb -o jsonpath="{.data.mongodb-root-password}" | base64 --decode)

To connect to your database, create a MongoDB&reg; client container:

    kubectl run --namespace default mongodb-client --rm --tty -i --restart='Never' --env="MONGODB_ROOT_PASSWORD=$MONGODB_ROOT_PASSWORD" --image docker.io/bitnami/mongodb:4.4.10-debian-10-r15 --command -- bash

Then, run the following command:
    mongo admin --host "mongodb" --authenticationDatabase admin -u root -p $MONGODB_ROOT_PASSWORD

To connect to your database from outside the cluster execute the following commands:

    kubectl port-forward --namespace default svc/mongodb 27017:27017 &
    mongo --host 127.0.0.1 --authenticationDatabase admin -p $MONGODB_ROOT_PASSWORD



Connect to MongoDB:

pegaz@ubuntu:~/mkube/chm1$ export MONGODB_ROOT_PASSWORD=$(kubectl get secret --namespace default mongodb -o jsonpath="{.data.mongodb-root-password}" | base64 --decode)

pegaz@ubuntu:~/mkube/chm1$ kubectl run --namespace default mongodb-client --rm --tty -i --restart='Never' --env="MONGODB_ROOT_PASSWORD=$MONGODB_ROOT_PASSWORD" --image docker.io/bitnami/mongodb:4.4.10-debian-10-r15 --command -- bash

If you don't see a command prompt, try pressing enter.

I have no name!@mongodb-client:/$ hostname 

mongodb-client

I have no name!@mongodb-client:/$ du -hs /bitnami/mongodb/data/

4.0K	/bitnami/mongodb/data/





