Apply all manifests:

```bash
kubectl apply -f serviceaccount.yaml
kubectl apply -f role.yaml
kubectl apply -f rolebinding.yaml
kubectl auth can-i list pods --as=system:serviceaccount:default:pod-reader -n default
```

This lab focuses on Kubernetes authorization with RBAC.

