Example debugging flow:

```bash
kubectl apply -f deployment-broken.yaml
kubectl rollout status deployment/bad-web
kubectl get pods -l app=bad-web
kubectl describe pods -l app=bad-web
kubectl get events --sort-by=.metadata.creationTimestamp
```

The rollout fails because image `nginx:9.99` does not exist.

Use the fixed manifest in `deployment.yaml`, or update the image with:

```bash
kubectl set image deployment/bad-web web=nginx:1.27
kubectl rollout status deployment/bad-web
kubectl rollout history deployment/bad-web
```

