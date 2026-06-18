Apply all manifests:

```bash
kubectl apply -f deploy-stable.yaml
kubectl apply -f deploy-canary.yaml
kubectl apply -f service.yaml
kubectl get deploy -l app=payments
kubectl get pods -l app=payments --show-labels
```

Traffic split is approximated by replica ratio (5 stable : 1 canary).

