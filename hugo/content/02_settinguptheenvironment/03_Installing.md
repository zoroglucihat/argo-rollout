+++
title = "Setting up the Environment"
menuTitle = "2.3 Installing"
weight = 3
url = "03_Installing"
+++

## 2.3 Installing Argo Rollouts
``` 
# Step 1 
kubectl create namespace argo-rollouts

# Step 2

kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml

# Run this command for test:
kubectl get crd | grep rollouts 

#Output should look like this: 
rollouts.argoproj.io                             2023-04-26T22:22:40Z
``` 



