## Imperative Method

### Create Deployment and save manifest to deployment.yaml:

```bash
kubectl create deployment api-deploy \
  --image=nginx:1.27 \
  --replicas=3 \
  --dry-run=client -o yaml > deployment.yaml
```

Then manually edit `deployment.yaml` to add the `tier: backend` label to both `matchLabels` and Pod template labels.

Or use this command to add the label after generation:

```bash
kubectl patch -f deployment.yaml -p '{"spec":{"selector":{"matchLabels":{"tier":"backend"}},"template":{"metadata":{"labels":{"tier":"backend"}}}}}' --dry-run=client -o yaml > deployment.yaml
```
Using kubectl patch (JSON Patch):
```bash
kubectl patch deployment web-deploy --type='json' -p='[
  {
    "op": "add",
    "path": "/spec/template/metadata/labels/tier",
    "value": "backend"
  }
]'
```
Using kubectl patch (Strategic Merge):

```bash
kubectl patch deployment web-deploy -p '{"spec":{"template":{"metadata":{"labels":{"tier":"backend"}}}}}'
```

### Create Service:

```bash
kubectl expose deployment api-deploy \
  --name=api-svc \
  --port=80 \
  --dry-run=client -o yaml > service.yaml
```

Then manually edit `service.yaml` to add the `tier: backend` selector.

---

## Declarative Method

Apply both manifests:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get deploy api-deploy
kubectl get svc api-svc
kubectl get pods -l app=api,tier=backend
```

Verify the Service endpoints:
```bash
kubectl get endpoints api-svc
```



