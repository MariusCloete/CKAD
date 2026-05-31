Apply both manifests:

```bash
kubectl apply -f crd.yaml
kubectl apply -f widget.yaml
kubectl get crd widgets.example.com
kubectl get widgets
```

