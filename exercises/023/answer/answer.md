Apply both manifests:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get deploy web-deploy
kubectl get svc web-svc
```

