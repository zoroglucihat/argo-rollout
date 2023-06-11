+++
title = "Setting up the Environment"
menuTitle = "2.2 Installing"
weight = 4
url = "/02_settingUpTheEnvironment/02_Installing"
+++

## 2.1 Installation
#### Kubectl Plugin Installation

#### Brew (MacOS)
<pre><code class="shell">
brew install argoproj/tap/kubectl-argo-rollouts
</code></pre>
#### Chocolatey (Windows)
<pre><code class="shell">
choco install kubernetes-cli
</code></pre>


#### Manual

Install Argo Rollouts Kubectl plugin with curl.

<pre><code class="shell">
curl -LO https://github.com/argoproj/argo-rollouts/releases/latest/download/kubectl-argo-rollouts-darwin-amd64
</code></pre>

{{% notice tip %}}
For Linux dist, replace darwin with linux
{{% /notice %}}


Make the kubectl-argo-rollouts binary executable.

<pre><code class="shell">
chmod +x ./kubectl-argo-rollouts-darwin-amd64
</code></pre>
Move the binary into your PATH.
<pre><code class="shell">
sudo mv ./kubectl-argo-rollouts-darwin-amd64 /usr/local/bin/kubectl-argo-rollouts
</code></pre>
Test to ensure the version you installed is up-to-date:
<pre><code class="shell">
kubectl argo rollouts version
</code></pre>


#### Controller Installation
<pre><link rel="stylesheet" href="/css/style.css"> <code class="shell">
 kubectl create namespace argo-rollouts
 
 kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml
</code></pre>
After installing argo rollouts, run this command
<pre><code class="shell">
kubectl get crd | grep rollouts
</code></pre>
</code></pre>
If you are seeing this types of output, argo rollouts has successfully installed
<pre><code class="shell">
rollouts.argoproj.io 2023-04-26T22:22:40Z
</code></pre>


{{% notice tip %}}
If you are using another namespace name, please update install.yaml clusterrolebinding's serviceaccount namespace name.
{{% /notice %}}

{{% notice tip %}}
When installing Argo Rollouts on Kubernetes v1.14 or lower, the CRD manifests must be kubectl applied with the --validate=false option. This is caused by use of new CRD fields introduced in v1.15, which are rejected by default in lower API servers.
{{% /notice %}}

{{% notice tip %}}
Argo Rollouts CRDs are not included into namespace-install.yaml. and have to be installed separately. The CRD manifests are located in manifests/crds directory. Use the following command to install them:
<br>kubectl apply -k https://github.com/argoproj/argo-rollouts/manifests/crds\?ref\=stable</br>

{{% /notice %}}

