Apply the manifest and perform the update:

```bash
kubectl apply -f deployment.yaml
kubectl set image deployment/web-rollout web=nginx:1.27.1
kubectl rollout status deployment/web-rollout
kubectl rollout history deployment/web-rollout
```

