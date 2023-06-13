+++
title = "BLUE GREEN DEPLOYMENT"
menuTitle = "3.2 Deployment Examples"
weight = 2
url = "03_blueGreenDeployment/02_deployment"
+++

## 3.2 Deployment Examples

<link rel="stylesheet" href="/css/custom.css">

#### Rollout yaml file 
<pre><link rel="stylesheet" href="/css/style.css"> <code class="yaml">
apiVersion: argoproj.io/v1alpha1
kind: Rollout
metadata:
  name: nginx-bluegreen
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
        image: nginx:1.19.3
        ports:
        - containerPort: 80
  strategy:
    blueGreen:
      activeService: nginx-active-svc
      previewService: nginx-preview-svc
      autoPromotionEnabled: true
</code></pre>

#### Service yaml file
#### Service yaml file
<pre><link rel="stylesheet" href="/css/style.css"> <code class="yaml">
apiVersion: v1
kind: Service
metadata:
  name: nginx-active-svc
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
  name: nginx-preview-svc
  namespace: argo-rollouts
spec:
  selector:
    app: nginx
  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
</code></pre>
