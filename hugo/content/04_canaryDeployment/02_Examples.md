+++
title = "CANARY DEPLOYMENT"
menuTitle = "4.2 Deployment Examples"
weight = 2
url = "04_canaryDeployment/02_Examples"
url = "04_canaryDeployment/02_Examples"
+++

## 4.2 Deployment Examples

<link rel="stylesheet" href="/css/custom.css">

#### Rollout yaml file
<pre><link rel="stylesheet" href="/css/style.css"> <code class="yaml">
apiVersion: argoproj.io/v1alpha1
kind: Rollout
metadata:
  name: nginx-canary
  namespace: argo-rollouts
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.19.10
        ports:
        - containerPort: 80
  strategy:
    canary:
      steps:
      - setWeight: 25
      - pause: {duration: 30s}
      - setWeight: 50
      - pause: {duration: 30s}
      - setWeight: 75
      - pause: {duration: 30s}
      - setWeight: 100
      canaryService: nginx-canary-svc
      stableService: nginx-stable-svc
</code></pre>

#### Service yaml file
#### Service yaml file
<pre><link rel="stylesheet" href="/css/style.css"> <code class="yaml">
# nginx-services.yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-stable-svc
  namespace: argo-rollouts
spec:
  selector:
    app: nginx
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: nginx-canary-svc
  namespace: argo-rollouts
spec:
  selector:
    app: nginx
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
</code></pre>
