# ⚙️ Perform a Rolling Update for a Kubernetes Deployment

Setup 
```bash
kubectl create deployment web-app --image=nginx:1.19 --replicas=3
```

You have a Deployment named `web-app` running the `nginx:1.19` image with 3 replicas. Perform a rolling update to upgrade the image to `nginx:1.21` while ensuring zero downtime.

Provide the `kubectl` commands required to achieve this.