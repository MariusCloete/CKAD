Apply both manifests:

```bash
kubectl apply -f pvc.yaml
kubectl apply -f deployment.yaml
kubectl get pvc web-data-pvc
kubectl get deploy web-data-deploy
```

