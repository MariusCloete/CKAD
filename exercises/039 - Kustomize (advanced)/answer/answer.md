Apply overlays:

```bash
kubectl apply -k overlays/dev
kubectl apply -k overlays/prod
kubectl get deploy | findstr web
```

