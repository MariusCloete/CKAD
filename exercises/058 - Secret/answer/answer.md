Apply both manifests:

```bash
kubectl apply -f secret.yaml
kubectl apply -f pod.yaml
kubectl get secret db-secret
kubectl logs secret-demo
```

