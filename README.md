# Kubernetes Work

## Prereqs (Windows)
### Install Chocolatey
```
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

### Install Virtualbox
```
choco install virtualbox --version=6.0.14 --params "/ExtensionPack"
```

### Install Vagrant
```
choco install vagrant
```

### Install latest kubectl version (Windows via PowerShell)
```
choco install kubernetes-cli
```

### Install Helm if desired
```
choco install kubernetes-helm
```

## Run Vagrantfile to create cluster
### In PowerShell, cd to Vagrantfile directory (Vagrant\CentOS)
Review Vagrantfile code and update as needed
```
vagrant up
```

## Post cluster setup
### Getting Kube Config
#### From Bash prompt in VSCode - update remotehost and local path values
##### Username: vagrant     Password: vagrant
```
rm /c/Users/user_name/.ssh/known_hosts
scp vagrant@172.30.250.55:/home/vagrant/.kube/config /c/Users/user_name/.kube
```

### Add master node IP to your hosts file
##### Windows - C:\Windows\System32\drivers\etc\hosts
##### Linux - /etc/hosts
```
MASTER_NODE_IP	k8s-master
NODE_1_IP	k8s-node-1
NODE_2_IP	k8s-node-2
```

### Test connectivity
```
kubectl config view
kubectl get nodes
```

### SSH into nodes
```
ssh-keygen -t rsa -b 2048

ssh-copy-id vagrant@k8s-master
ssh-copy-id vagrant@k8s-node-1
ssh-copy-id vagrant@k8s-node-2

ssh vagrant@k8s-master
ssh vagrant@k8s-node-1
ssh vagrant@k8s-node-2
```
