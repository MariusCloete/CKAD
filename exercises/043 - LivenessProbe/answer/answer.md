Apply the Pod manifest:

```bash
kubectl apply -f pod.yaml
kubectl get pod probe-pod
kubectl describe pod probe-pod
```

Check the `Liveness` and `Readiness` sections in the Pod description.

