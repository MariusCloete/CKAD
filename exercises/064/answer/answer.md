Example troubleshooting flow:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service-broken.yaml
kubectl get svc selector-demo-svc
kubectl get endpoints selector-demo-svc
kubectl describe svc selector-demo-svc
kubectl apply -f service.yaml
kubectl get endpoints selector-demo-svc
```

