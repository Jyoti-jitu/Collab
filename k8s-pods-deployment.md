# 🚀 Kubernetes Nginx Practice Guide

This guide walks through:

-   Creating namespace\
-   Running pods\
-   Executing commands inside pods\
-   Creating deployments\
-   Cleaning resources

------------------------------------------------------------------------

# 📦 1. Run Nginx Pod (quick test)

``` bash
kubectl run nginx --image=nginx:latest -n nginx
```

Delete the pod:

``` bash
kubectl delete pod nginx -n nginx
```

Delete namespace:

``` bash
kubectl delete ns nginx
```

Create namespace from YAML:

``` bash
kubectl apply -f namespace.yml
```

------------------------------------------------------------------------

# 🧱 2. Create Pod using YAML

### 📄 pod.yml

``` yaml
kind: Pod
apiVersion: v1
metadata:
  name: nginx-pod
  namespace: nginx
spec:
  containers:
    - name: nginx
      image: nginx:latest
      ports:
        - containerPort: 80
```

Apply pod:

``` bash
kubectl apply -f pod.yml
```

------------------------------------------------------------------------

# 🔧 3. Execute Inside Pod

``` bash
kubectl exec -it nginx-pod -n nginx -- bash
```

Describe pod:

``` bash
kubectl describe pod/nginx-pod -n nginx
```

Delete pod:

``` bash
kubectl delete pod nginx-pod -n nginx
```

------------------------------------------------------------------------

# 🚀 4. Create Deployment

### 📄 deployment.yml

``` yaml
kind: Deployment
apiVersion: apps/v1
metadata:
  name: nginx-deployment
  namespace: nginx
spec:
  replicas: 2
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
          image: nginx:latest
          ports:
            - containerPort: 80
```

Apply deployment:

``` bash
kubectl apply -f deployment.yml
```

Check deployment:

``` bash
kubectl get deployment -n nginx
```

------------------------------------------------------------------------

# 🧹 5. Cleanup Resources

Delete deployment:

``` bash
kubectl delete deployment nginx-deployment -n nginx
```

Delete namespace (removes everything):

``` bash
kubectl delete ns nginx
```

------------------------------------------------------------------------

# ✅ Completed

You now understand:

-   Pods vs Deployments\
-   Namespace isolation\
-   Container execution in Kubernetes\
-   Scaling using deployments
