Apply the Pod manifest:

```bash
kubectl apply -f pod.yaml
kubectl get pod init-demo
kubectl logs init-demo -c app
```

