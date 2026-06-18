Apply the Ingress manifest:

```bash
kubectl apply -f ingress.yaml
kubectl get ingress web-ingress
kubectl describe ingress web-ingress
```

This example uses `networking.k8s.io/v1`, which replaces older deprecated Ingress API versions.

