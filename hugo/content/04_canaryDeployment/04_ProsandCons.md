+++
title = "CANARY DEPLOYMENT"
menuTitle = "4.4 Pros and Cons"
weight = 2
url = "04_canaryDeployment/04_ProsAndCons"
+++


### 4.4 Pros and Cons:

#### Pros

<b>Reduces risks:</b> Canary Deployment prevents any new app or update from being made available to all users instantly, preventing unexpected bugs or issues from affecting all users.

<b>Detects issues:</b> Testing on a small subset measures the performance and compatibility of the new release, allowing to detect potential issues earlier.

<b>Improves user experience:</b> Providing early access to users on a small subset to test new features or interface improves user experience.

<b>Prevents scaling issues:</b> In high traffic or unexpected loading situations, testing new infrastructure on a small subset is helpful to detect and prevent scaling issues.

#### Cons

<b>Additional resource requirements:</b> Canary Deployment requires additional resources to create and manage a subset. This can increase operational costs.

<b>Additional management requirements:</b> Managing and controlling a new subset requires a team's time and resources.

<b>Data integrity issues</b> During Canary Deployment, data consistency issues between old and new versions can occur.
* User dissatisfaction: While testing the new version, users of a subset may not be able to access the new version. In this case, users may experience dissatisfaction due to not being able to access new features.

<b>Additional time and effort requirements:</b> Canary Deployment requires additional time and effort to run additional testing, resolve issues, and deliver the new version to end users.

These disadvantages can be minimized with proper implementation of Canary Deployment, careful performance and compatibility testing, and consideration of user experience.