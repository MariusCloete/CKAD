Apply both manifests:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get deploy api-deploy
kubectl get svc api-svc
```

