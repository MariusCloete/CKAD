Apply both manifests:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get deploy web-clusterip
kubectl get svc web-clusterip-svc
kubectl get endpoints web-clusterip-svc
```

