Apply and manage rollout:

```bash
kubectl apply -f deployment.yaml
kubectl rollout pause deployment/checkout
kubectl set image deployment/checkout web=nginx:1.27.1
kubectl rollout resume deployment/checkout
kubectl rollout status deployment/checkout
kubectl rollout undo deployment/checkout
```

