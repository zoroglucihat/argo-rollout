+++
title = "Setting up the Environment"
menuTitle = "2.2 Installing Argo Rollout CLI"
weight = 2
url = "02_InstallingCLi"
+++

## 2.2 Installing Argo Rollouts CLI
There are two types of installation. Before installing argo rollouts on cluster/s it argo-rollouts cli must be installed on your device.

<strong>Argo rollouts cli installation for macOS; </strong>
```
#step 1
brew install argoproj/tap/kubectl-argo-rollouts
#step 2
chmod +x ./kubectl-argo-rollouts-darwin-amd64
#step 3
sudo mv ./kubectl-argo-rollouts-darwin-amd64 /usr/local/bin/kubectl-argo-rollouts
#Make sure that is installed or not
kubectl argo rollouts version
```

<strong>Argo rollouts cli installation for Windows; </strong>
</strong>
```
#Download the latest version https://github.com/argoproj/argo-rollouts/releases
#Extract zip and run powershell command
setx PATH "%PATH%;C:\path\to\argo-rollouts" /M

# test the installation
argo-rollouts version


```





