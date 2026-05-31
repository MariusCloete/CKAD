Apply manifests and switch traffic:

```bash
kubectl apply -f deploy-blue.yaml
kubectl apply -f deploy-green.yaml
kubectl apply -f service.yaml
kubectl patch service shop-svc -p '{"spec":{"selector":{"app":"shop","version":"green"}}}'
kubectl get svc shop-svc -o yaml
```

