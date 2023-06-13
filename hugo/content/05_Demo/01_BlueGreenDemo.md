+++
title = "BlueGreen Demo"
pre = "5.1 "
weight = 11
url="05_Demo/01_BlueGreenDemo"

+++

## 5.1	Blue Green 

<link rel="stylesheet" href="/css/custom.css">
<p id="main-text">To gain firsthand knowledge of how Argo Rollouts manages blue-green deployments, we'll proceed to launch a sample application. This application comprises Rollouts, Service, and Ingress, functioning as Kubernetes objects.</p>


<b>rollout.yaml</b>
<pre><link rel="stylesheet" href="/css/style.css"> <code class="yaml scrollable">
# This example demonstrates a Rollout using the blue-green update strategy, which contains a manual
# gate before promoting the new stack.
apiVersion: argoproj.io/v1alpha1
kind: Rollout
metadata:
  name: rollout-bluegreen
spec:
  replicas: 2
  revisionHistoryLimit: 2
  selector:
    matchLabels:
      app: rollout-bluegreen
  template:
    metadata:
      labels:
        app: rollout-bluegreen
    spec:
      containers:
      - name: rollouts-demo
        image: argoproj/rollouts-demo:blue
        imagePullPolicy: Always
        ports:
        - containerPort: 8080
  strategy:
    blueGreen: 
      # activeService specifies the service to update with the new template hash at time of promotion.
      # This field is mandatory for the blueGreen update strategy.
      activeService: rollout-bluegreen-active
      # previewService specifies the service to update with the new template hash before promotion.
      # This allows the preview stack to be reachable without serving production traffic.
      # This field is optional.
      previewService: rollout-bluegreen-preview
      # autoPromotionEnabled disables automated promotion of the new stack by pausing the rollout
      # immediately before the promotion. If omitted, the default behavior is to promote the new
      # stack as soon as the ReplicaSet are completely ready/available.
      # Rollouts can be resumed using: `kubectl argo rollouts promote ROLLOUT`
      autoPromotionEnabled: false
</code></pre>

<b>service.yaml</b>
<pre><link rel="stylesheet" href="/css/style.css"> <code class="yaml scrollable">
kind: Service
apiVersion: v1
metadata:
  name: rollout-bluegreen-active
spec:
  selector:
    app: rollout-bluegreen
  ports:
  - protocol: TCP
    port: 80
    targetPort: 8080

---
kind: Service
apiVersion: v1
metadata:
  name: rollout-bluegreen-preview
spec:
  selector:
    app: rollout-bluegreen
  ports:
  - protocol: TCP
    port: 80
    targetPort: 8080
</code></pre>


<b>ingress.yaml</b>
<pre><link rel="stylesheet" href="/css/style.css"> <code class="yaml scrollable">
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: rollout-bluegreen
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
            name: rollout-bluegreen-active
            port:
              number: 80
</code></pre>

#### Let's apply and test it blue green deployment now.


<p id="main-text">
Let's deploy the every components we need.
</p>
<pre><code class="shell">
kubectl apply -f argo-rollouts-example/blue-green-deployment-example/
</code></pre>

<p id="main-text">
You can see the current status of this rollout by running below command as well
</p>

<pre><code class="shell">
kubectl argo rollouts get rollout rollout-bluegreen
</code></pre>

<p id="main-text"> Now, we deploy the green version of the app </p>

<pre><code class="shell">
kubectl argo rollouts set image rollout-bluegreen rollouts-demo=argoproj/rollouts-demo:green
</code></pre>

<p id="main-text"> by running the command below, which shows, the new version is in "paused" state </p>

<pre><code class="shell">
kubectl argo rollouts get rollout rollout-bluegreen
</code></pre>

<p id="main-text"> promote the green version of our app </p>

<pre><code class="shell">
kubectl argo rollouts promote rollout-bluegreen
</code></pre>


#### how to rollback to first revision which is blue


<p id="main-text"> Undo a rollout </p>

<pre><code class="shell">
kubectl argo rollouts undo rollout-bluegreen
</code></pre>

<p id="main-text"> Undo a rollout revision 2 </p>

<pre><code class="shell">
kubectl argo rollouts undo rollout-bluegreen --to-revision=2
</code></pre>




Undo a rollout revision 2
kubectl argo rollouts undo rollout-bluegreen --to-revision=2
</code></pre>