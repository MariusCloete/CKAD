Example troubleshooting flow:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service-broken.yaml
kubectl describe svc port-demo-svc
kubectl get endpoints port-demo-svc
kubectl apply -f service.yaml
kubectl describe svc port-demo-svc
```

