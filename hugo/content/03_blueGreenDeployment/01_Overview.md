+++
title = "BLUE GREEN DEPLOYMENT"
menuTitle = "3.1 Overview"
weight = 1
url = "03_blueGreenDeployment/01_Overview"
+++

## 3.1 Overview

<link rel="stylesheet" href="/css/custom.css">
<p id="main-text">
In Blue-Green deployments, the Rollout controller manages ReplicaSets and modifies Service resources. Users specify an active service for regular traffic and an optional preview service for new version traffic. The controller ensures traffic routing by updating service selectors with a unique ReplicaSet hash, defining active and preview stacks.
</p>
<img src="/images/blue-green.png" alt="My Image" />