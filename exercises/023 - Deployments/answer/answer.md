Apply both manifests:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get deploy web-deploy
kubectl get svc web-svc
```

imperative commands:

```bash
kubectl create deployment web-deploy --image=nginx:1.27 --replicas=3 --labels=app=web --dry-run=client -o yaml > deployment.yaml
kubectl apply -f deployment.yaml
kubectl expose deployment web-deploy --name=web-svc --port=80 --target-port=80
kubectl get deploy web-deploy
kubectl get svc web-svc
```

