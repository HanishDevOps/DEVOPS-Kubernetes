# DEVOPS-Kubernetes

Kubernetes is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. It provides a robust and flexible environment for running and managing container workloads.

--- KUBERNETES Install Steps ---


## Step1:

### On Master and slave


1. apt-get update -y
2. apt-get install docker.io -y
3. service docker restart
4. curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
5. echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" >/etc/apt/sources.list.d/kubernetes.list
6. apt-get update
7. apt install kubeadm=1.20.0-00 kubectl=1.20.0-00 kubelet=1.20.0-00 -y

----------------------------------------------------------------------------------------------------------------------------
## Step2:
On Master node:

kubeadm init --pod-network-cidr=192.168.0.0/16
-----------------------------------------------------------------------------------------------------------------------------
## Step3:

On Master node:
1. mkdir -p $HOME/.kube
2. sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
3. sudo chown $(id -u):$(id -g) $HOME/.kube/config
--------------------------------------------------------------------------------------------------------------------------------
Step4:

On Master node:
1. kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.1/manifests/calico.yaml
2. kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.49.0/deploy/static/provider/baremetal/deploy.yaml
