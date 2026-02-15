# Steps to create Cluster 
```bash
mkdir kind-cluster
```

## Code to create Cluster 

```bash
vim config.yml
```

```yml
kind: Cluster 
apiVersion: kind.x-k8s.io/v1alpha4

nodes:
- role: control-plane
  image: kindest/node:v1.35.0
- role: worker 
  image: kindest/node:v1.35.0
- role: worker 
  image: kindest/node:v1.35.0
- role: worker
  image: kindest/node:v1.35.0
  extraPortMappings:
  - containerPort: 80
    hostPort: 80 
    protocol: TCP
```


## command to start Cluster 

```bash
$ kind create cluster --name=tws-cluster --config=config.yml
```

```output
Creating cluster "tws-cluster" ...
 ✓ Ensuring node image (kindest/node:v1.35.0) 🖼 ^[[B
 ✓ Preparing nodes 📦 📦 📦 📦  
 ✓ Writing configuration 📜 
 ✓ Starting control-plane 🕹️ 
 ✓ Installing CNI 🔌 
 ✓ Installing StorageClass 💾 ^[[D
 ✓ Joining worker nodes 🚜 
Set kubectl context to "kind-tws-cluster"
You can now use your cluster with:

kubectl cluster-info --context kind-tws-cluster

Thanks for using kind! 😊
```

```bash
kubectl cluster-info --context kind-tws-cluster
```
