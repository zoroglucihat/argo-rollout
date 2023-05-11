+++
title = "BLUE GREEN DEPLOYMENT"
menuTitle = "3.3 Use Cases"
weight = 3
url = "03_blueGreenDeployment/03_blueGreenDeployment"
+++

## 3.3 Use Cases
-----

<b>Feature Releases and Upgrades</b>: Argo Rollouts' blue-green strategy is ideal for introducing new application versions or major upgrades. It enables seamless user transition to new versions and quick reversion in case of issues, ensuring uninterrupted service.

<b>Bug Fixes and Patch Releases</b>: For immediate bug fixes or security patches, Argo Rollouts lets you validate a patched version of your app in parallel with the current version before transitioning user traffic.

<b>A/B Testing:</b> Blue-green strategy can be used for A/B testing major app changes. Argo Rollouts facilitates deployment to a user subset, allowing feedback collection before full rollout.

<b>Infrastructure Changes</b>: For major infrastructure changes like database schema alterations or server migrations, blue-green deployments offer a safety net. This strategy allows for setting up and testing new infrastructure before transitioning, ensuring stability and performance.