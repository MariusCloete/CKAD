Apply all manifests:

```bash
kubectl apply -f frontend.yaml
kubectl apply -f backend.yaml
kubectl apply -f networkpolicy.yaml
kubectl get networkpolicy allow-frontend-to-backend
kubectl describe networkpolicy allow-frontend-to-backend
```

