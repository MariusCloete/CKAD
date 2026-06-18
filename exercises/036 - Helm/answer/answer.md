Helm commands:

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm install web bitnami/nginx -n helm-lab --create-namespace -f values.yaml
helm list -n helm-lab
kubectl get pods -n helm-lab
```

