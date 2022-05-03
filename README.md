## Jarvis - Kubernetes Cluster

```bash
kind create cluster --config kind/jarvis.yaml
```

### Install ingress controller

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/kind/deploy.yaml
```


## Deploy ArgoCD cluster

### 1. Install ArgoCD 

```bash
kubectl create namespace argocd

kubectl apply -n argocd -f argocd/install.yaml
```

### 2. Create Ingress NGINX

```bash
kubectl create -n argocd -f argocd/ingress.yaml
```

### 3. Get admin password

```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```
