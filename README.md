# Kubernetes Work

## Prereqs (Windows)
### Install Chocolatey
```
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

### Install Virtualbox
```
choco install virtualbox
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
```
vagrant up
```

## Post cluster setup
### Getting Kube Config
#### From Bash prompt in VSCode - update remotehost and local path values
```
scp vagrant@remote.host.ip:/home/vagrant/.kube/config /local/path/to/.kube
```

### Test connectivity
```
kubectl config view
kubectl get nodes
```