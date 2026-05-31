Apply all manifests:

```bash
kubectl apply -f namespace.yaml
kubectl apply -f limitrange.yaml
kubectl apply -f resourcequota.yaml
kubectl describe limitrange default-limits -n team-a
kubectl describe resourcequota team-a-quota -n team-a
```

