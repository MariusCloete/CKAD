Apply both manifests:

```bash
kubectl apply -f namespace.yaml
kubectl apply -f pod.yaml
kubectl get ns secure-apps --show-labels
kubectl describe pod secure-nginx -n secure-apps
```

This lab focuses on admission control through Pod Security Admission labels.

