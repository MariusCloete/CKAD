Apply all manifests:

```bash
kubectl apply -f frontend-deployment.yaml
kubectl apply -f api-deployment.yaml
kubectl apply -f frontend-service.yaml
kubectl apply -f api-service.yaml
kubectl apply -f ingress.yaml
kubectl get ingress apps-ingress
kubectl describe ingress apps-ingress
```

