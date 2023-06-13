+++
title = "Introduction to Argo Rollouts"
menuTitle = "1.3 Deployment Strategies"
weight = 17
description = "Illustrates the stakeholders of DokChess and their respective intentions."
url = "/01_introduction/03_DeploymentStrategies"
+++

### 1.3 Deployment Strategies
<link rel="stylesheet" href="/css/custom.css">

|Blue-Green Deployments|
|---------------------|
|Two separate environments (blue and green) with different application versions.
|All traffic initially directed to the blue environment (current version).
|New version deployed to the green environment.
|Traffic switched from blue to green after testing and validation.
|Minimal downtime during deployment.
|Instant rollback by switching traffic back to the blue environment if needed.

|Canary|
|---------------------|
|New version rolled out alongside the old version.
|Small percentage of traffic initially directed to the new version (canary).
|Controlled testing with a subset of users.
|Gradual traffic shift to the new version if it performs well.
|Eventually, the new version handles all traffic.
|Quick traffic reversion to the old version if issues arise during the rollout.