+++
title = "CANARY DEPLOYMENT"
menuTitle = "4.4 ProsAndCons"
weight = 2
url = "04_context/04_ProsAndCons"
+++


### Pros and Cons:
Here are the advantages and disadvantages of Canary Deployment:
Advantages:
* Reduces risks: Canary Deployment prevents any new app or update from being made available to all users instantly, preventing unexpected bugs or issues from affecting all users.
* Detects issues: Testing on a small subset measures the performance and compatibility of the new release, allowing to detect potential issues earlier.
* Improves user experience: Providing early access to users on a small subset to test new features or interface improves user experience.
* Prevents scaling issues: In high traffic or unexpected loading situations, testing new infrastructure on a small subset is helpful to detect and prevent scaling issues.
Disadvantages:
* Additional resource requirements: Canary Deployment requires additional resources to create and manage a subset. This can increase operational costs.
* Additional management requirements: Managing and controlling a new subset requires a team's time and resources.
* Data integrity issues: During Canary Deployment, data consistency issues between old and new versions can occur.
* User dissatisfaction: While testing the new version, users of a subset may not be able to access the new version. In this case, users may experience dissatisfaction due to not being able to access new features.
* Additional time and effort requirements: Canary Deployment requires additional time and effort to run additional testing, resolve issues, and deliver the new version to end users.

 These disadvantages can be minimized with proper implementation of Canary Deployment, careful performance and compatibility testing, and consideration of user experience.
