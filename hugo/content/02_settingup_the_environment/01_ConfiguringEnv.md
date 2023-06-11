+++
title = "Setting up the Environment"
menuTitle = "2.1 Configuring the Environment"
weight = 3
url = "/02_settingUpTheEnvironment/01_ConfiguringEnv"
+++

## 2.1 Configuring the Environment

<link rel="stylesheet" href="/css/custom.css">
<link rel="stylesheet" href="/css/text.css">

* **Prepare your Kubernetes cluster:** Ensure you have a Kubernetes cluster up and running. You can use managed Kubernetes services like Google Kubernetes Engine (GKE), Amazon Elastic Kubernetes Service (EKS), or Azure Kubernetes Service (AKS), or set up your own cluster using tools like kubeadm, minikube, or kind.

* **Install kubectl:** Ensure that you have the Kubernetes command-line tool, kubectl, installed on your machine and configured to interact with your cluster. Follow the official kubectl installation guide for instructions.

* **Install Argo Rollouts:** Install the Argo Rollouts controller and required Custom Resource Definitions (CRDs) on your Kubernetes cluster by following the official Argo Rollouts installation guide.


{{% notice note %}}
We will delve into a more detailed discussion on the installation process of Argo Rollouts in the upcoming section.
{{% /notice %}}
