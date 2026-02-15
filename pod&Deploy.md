```bash
kubectl run nginx  --image=nginx:latest -n nginx

```

```bash
kubectl delete pod nginx -n nginx


```
```bash
kubectl delete ns nginx

```
```bash
kubectl apply -f namespace.yml

```


```bash
#pod.yml
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
```bash
#to ececute 
kubectl apply -f pod.yml
```

```bash
kubectl exec -it nginx-pod -n nginx --bash 

```
```bash
kubectl describe pod/nginx-pod -n nginx

```

```bash
Events:
  Type    Reason     Age    From               Message
  ----    ------     ----   ----               -------
  Normal  Scheduled  8m39s  default-scheduler  Successfully assigned nginx/nginx-pod to tws-cluster-worker3
  Normal  Pulling    8m38s  kubelet            Pulling image "nginx:latest"
  Normal  Pulled     8m36s  kubelet            Successfully pulled image "nginx:latest" in 2.546s (2.546s including waiting). Image size: 62939286 bytes.
  Normal  Created    8m36s  kubelet            Container created
  Normal  Started    8m36s  kubelet            Container started 


```

```bash
kubectl delete pod nginx-pod -n nginx

```
```bash
#deployment.yml

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
```bash
kubectl apply -f deployment.yml

```
```bash
kubectl get deployment -n nginx

```

```bash

kubectl delete -f deployment.yml -n nginx
```

```bash


```
```bash


```
```bash


```
```bash


```
```bash


```
```bash


```
```bash


```
