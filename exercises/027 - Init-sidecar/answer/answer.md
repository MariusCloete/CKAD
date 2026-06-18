Apply the Pod manifest and verify sidecar output:

```bash
kubectl apply -f pod.yaml
kubectl logs sidecar-log-pod -c log-reader
```

