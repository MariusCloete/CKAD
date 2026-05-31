Apply all manifests:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl apply -f ingress.yaml
kubectl get ingress ingress-web
kubectl describe ingress ingress-web
```

