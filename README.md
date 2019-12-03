Work related to Kubernetes

### Prereqs (Windows)
# Install Chocolatey
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

# Install Virtualbox
choco install virtualbox

# Install Vagrant
choco install vagrant

# Install latest kubectl version (Windows via PowerShell)
choco install kubernetes-cli

# Install Helm if desired
choco install kubernetes-helm


### Run Vagrantfile to create cluster
# In PowerShell, cd to Vagrantfile directory (Vagrant\CentOS)
vagrant up


### Post cluster setup
# Getting Kube Config - update remotehost and local dir values
scp vagrant@remotehost.edu:/home/vagrant/.kube/config /local/dir

# Test connectivity
kubectl config view
kubectl get nodes
