Apply both manifests:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get svc web-nodeport-svc
kubectl describe svc web-nodeport-svc
```

