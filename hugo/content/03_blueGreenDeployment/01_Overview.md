+++
title = "BLUE GREEN DEPLOYMENT"
menuTitle = "3.1 Overview"
weight = 1
url = "01_Overview/03_blueGreenDeployment"
+++

## 3.1 Overview
-----

In Blue-Green deployments, the Rollout controller manages ReplicaSets and modifies Service resources. Users specify an active service for regular traffic and an optional preview service for new version traffic. The controller ensures traffic routing by updating service selectors with a unique ReplicaSet hash, defining active and preview stacks.

When the rollout's .spec.template changes, a new ReplicaSet is created. The active service initially points to the old ReplicaSet and switches to the new one once it's available. After a configured delay, the controller scales down the old ReplicaSet. This process enables seamless updates with minimal downtime and easy rollback.

<img src="/images/blue-green.png" alt="My Image" />