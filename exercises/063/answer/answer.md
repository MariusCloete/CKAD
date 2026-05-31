Apply both manifests:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get svc api-service-demo-svc
kubectl get endpoints api-service-demo-svc
```

