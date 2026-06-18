Apply the Pod manifest:

```bash
kubectl apply -f pod.yaml
kubectl get pod slow-start-pod
kubectl describe pod slow-start-pod
```

Check the `Startup` and `Readiness` probe results in the Pod description.

