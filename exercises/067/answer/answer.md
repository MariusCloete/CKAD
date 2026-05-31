Apply both manifests:

```bash
kubectl apply -f pod.yaml
kubectl apply -f networkpolicy.yaml
kubectl get networkpolicy deny-backend-ingress
kubectl describe networkpolicy deny-backend-ingress
```

