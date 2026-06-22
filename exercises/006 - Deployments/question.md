# ⚙️ Scale a Kubernetes Deployment

Setup
```bash
kubectl create deployment api-server --image=node:14 --replicas=1
```

You have a Deployment named `api-server` running the `node:14` image with 2 replicas. Scale the Deployment to handle increased traffic by increasing the number of replicas to 2.

Provide the `kubectl` commands required to achieve this.