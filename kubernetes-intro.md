# 🚀 Create Kubernetes Cluster using kind

## 📁 Step 1 --- Create Project Directory

``` bash
mkdir kind-cluster
cd kind-cluster
```

------------------------------------------------------------------------

## ⚙️ Step 2 --- Create Cluster Configuration File

Create config file:

``` bash
vim config.yml
```

Paste the following configuration:

``` yaml
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

------------------------------------------------------------------------

## 🏗️ Step 3 --- Create the Cluster

``` bash
kind create cluster --name tws-cluster --config config.yml
```

------------------------------------------------------------------------

## 🔍 Step 4 --- Verify Cluster

``` bash
kubectl cluster-info --context kind-tws-cluster
kubectl get nodes
```

------------------------------------------------------------------------

## 🔄 Step 5 --- Switch kubectl Context

``` bash
kubectl config use-context kind-tws-cluster
```

------------------------------------------------------------------------

## 🚀 Step 6 --- Deploy Test Pod

``` bash
kubectl run nginx --image=nginx:latest
kubectl get pods
```

------------------------------------------------------------------------

## 📦 Step 7 --- Useful Commands

### View namespaces

``` bash
kubectl get namespaces
kubectl get ns
```

### View system pods

``` bash
kubectl get pods -n kube-system
```

### Create namespace

``` bash
kubectl create namespace nginx
```

------------------------------------------------------------------------

## ✅ Cluster Ready

You now have a working Kubernetes cluster with kind.
