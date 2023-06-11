+++
title = "Canary Demo"
pre = "5.2 "
weight = 12
url="05_Demo/02_CanaryDemo"

+++

## 5.1	Canary

<link rel="stylesheet" href="/css/custom.css">
<p id="main-text">To gain firsthand knowledge of how Argo Rollouts manages canary deployments, we'll proceed to launch a sample application. This application comprises Rollouts, Service, and Ingress, functioning as Kubernetes objects.</p>


<b>rollout.yaml</b>
<pre><link rel="stylesheet" href="/css/style.css"> <code class="yaml scrollable">
apiVersion: argoproj.io/v1alpha1
kind: Rollout
metadata:
  name: rollouts-canary
  namespace: argo-demo
spec:
  replicas: 5
  strategy:
    canary:
      steps:
      - setWeight: 20
      - pause: {}
      - setWeight: 40
      - pause: {duration: 10}
      - setWeight: 60
      - pause: {duration: 10}
      - setWeight: 80
      - pause: {duration: 10}
  revisionHistoryLimit: 2
  selector:
    matchLabels:
      app: rollouts-demo
  template:
    metadata:
      labels:
        app: rollouts-demo
    spec:
      containers:
      - name: rollouts-demo
        image: argoproj/rollouts-demo:blue
        ports:
        - name: http
          containerPort: 8080
          protocol: TCP
        resources:
          requests:
            memory: 32Mi
            cpu: 5m
</code></pre>

<b>service.yaml</b>
<pre><link rel="stylesheet" href="/css/style.css"> <code class="yaml scrollable">
apiVersion: v1
kind: Service
metadata:
  name: rollouts-canary
  namespace: argo-demo
spec:
  ports:
  - port: 80
    targetPort: http
    protocol: TCP
    name: http
  selector:
    app: rollouts-demo
</code></pre>


<b>ingress.yaml</b>
<pre><link rel="stylesheet" href="/css/style.css"> <code class="yaml scrollable">
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: rollout-canary
  annotations:
    kubernetes.io/ingress.class: nginx
spec:
  rules:
  - host: 
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: rollout-canary-active
            port:
              number: 80
</code></pre>

#### Let's apply and test it blue green deployment now.

<p id="main-text"> Let's deploy the every components we need. </p>

<pre><code class="shell">
kubectl apply -f argo/deployments/canary
</code></pre>

<p id="main-text"> You can see the current status of this rollout by running below command as well</p>

<pre><code class="shell">
kubectl argo rollouts get rollout rollout-canary
</code></pre>

<p id="main-text"> Now, we deploy the green version of the app </p>

<pre><code class="shell">
kubectl argo rollouts set image rollouts-demo rollouts-demo=argoproj/rollouts-demo:yellow
</code></pre>

<p id="main-text"> by running the command below, which shows, the new version is in "paused" state </p>

<pre><code class="shell">
kubectl argo rollouts get rollout rollout-canary
</code></pre>

<p id="main-text"> promote the green version of our app </p>

<pre><code class="shell">
kubectl argo rollouts promote rollout-canary
</code></pre>
