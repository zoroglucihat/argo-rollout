+++
title = "Canary Deployment"
menuTitle = "4.1 Overview"
weight = 1
url = "04_canaryDeployment/01_Overview"
+++

## 4.1 Overview
<link rel="stylesheet" href="/css/custom.css">
<p id="main-text">Argo Rollouts uses Kubernetes custom resources to implement canary deployment strategy. Argo Rollout source; defines the canary deployment strategy, and metrics in the background.<br><br>
Canary deployment steps are basically explain as follows. A certain percentage of new versions are run.
The traffic that will come to the new application is presented to a certain percentage of users.
The performance and errors in the new version of the application are checked.
If acceptance criteria are met, all traffic is submitted to the new application. If problems are encountered as a result of these tests, the tests are repeated and the problems are fixed.</p>



<img src="/images/canary.png" alt="Canary" />