Apply the Pod manifest:

```bash
kubectl apply -f pod.yaml
kubectl get pod cache-pod
kubectl exec cache-pod -- cat /cache/health.txt
```

Expected output from the last command:

```text
ok
```
Apply the Pod manifest:

```bash
kubectl apply -f pod.yaml
kubectl get pod cache-pod
kubectl exec cache-pod -- cat /cache/health.txt
```

Expected output from the last command:

```text
ok
```

