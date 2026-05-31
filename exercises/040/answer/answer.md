Render and apply staging overlay:

```bash
kubectl kustomize overlays/staging
kubectl apply -k overlays/staging
kubectl get deploy frontend -L env
kubectl get deploy frontend -o yaml | findstr owner
```

