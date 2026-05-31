Apply both manifests:

```bash
kubectl apply -f configmap.yaml
kubectl apply -f pod.yaml
kubectl get configmap app-config
kubectl logs config-demo
```

