Apply both manifests:

```bash
kubectl apply -f pvc.yaml
kubectl apply -f deployment.yaml
kubectl get pvc notes-pvc
kubectl get deploy notes-app
```

