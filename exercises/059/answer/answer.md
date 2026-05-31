Apply both manifests:

```bash
kubectl apply -f serviceaccount.yaml
kubectl apply -f pod.yaml
kubectl get sa app-sa
kubectl describe pod sa-demo
```

