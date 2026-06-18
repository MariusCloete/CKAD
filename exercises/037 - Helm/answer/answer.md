Upgrade and rollback commands:

```bash
helm upgrade web bitnami/nginx -n helm-lab -f values-v2.yaml
helm history web -n helm-lab
kubectl get deploy -n helm-lab
helm rollback web 1 -n helm-lab
helm history web -n helm-lab
```

