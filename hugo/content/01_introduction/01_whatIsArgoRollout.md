+++
title = "Introduction to Argo Rollouts"
menuTitle = "1.1 What is Argo Rollouts"
weight = 15
url = "/01_introduction/01_whatIsArgoRollout"
+++


<link rel="stylesheet" href="/css/custom.css">

### Key features of Argo Rollouts include
* Advanced Deployment Strategies
* Custom Resource Definitions (CRDs)
* Integration with Monitoring and Analysis Tools
* Automated Analysis and Rollback
* Flexible and Customizable
### Why Argo Rollouts needed?
<p id="main-text">
The Native Kubernetes Deployment object provides the rolling update strategy, which is useful for basic situation. Readiness probe gives you simple and fast checks. If the other checks like stress coming up in the table, it is not require a solution for our needs. Argo rollouts solve these problems:
</p>

 * It is possible to adjust the speed in rollout.
 * Control the flow of traffic.
 * Deep tests, stress tests and one-time checks.
 * Rollback is easy 

<!-- {{% notice tip %}}
Uygulamanın öne çıkan özellikleri
{{% /notice %}} -->