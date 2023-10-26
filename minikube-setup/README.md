
# Minikube Cluster creation steps

 ## What you’ll need(t2.medium)
 
2 CPUs or more

2GB of free memory

20GB of free disk space

Internet connection

Container or virtual machine manager, such as: Docker, QEMU, Hyperkit, Hyper-V, KVM, Parallels, Podman, VirtualBox, or VMware Fusion/Workstation

## kubectl (install)

```bash
curl -o kubectl https://amazon-eks.s3-us-west-2.amazonaws.com/1.14.6/2019-08-22/bin/linux/amd64/kubectl
chmod +x ./kubectl
mv kubectl /usr/bin
kubectl version --short --client
```

## Install docker:

```bash
yum install docker -y
service docker start
```

## Minikube setup:

```bash
curl -Lo minikube https://github.com/kubernetes/minikube/releases/download/v1.25.2/minikube-linux-amd64
chmod +x minikube
sudo mv minikube /usr/bin/
yum install conntrack -y
minikube start --driver=none
```

