Example troubleshooting flow:

```bash
kubectl apply -f deployment-broken.yaml
kubectl apply -f service.yaml
kubectl get endpoints label-demo-svc
kubectl get pods --show-labels
kubectl apply -f deployment.yaml
kubectl get endpoints label-demo-svc
```

