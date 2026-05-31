Apply the custom resource:

```bash
kubectl apply -f backuppolicy.yaml
kubectl get backuppolicies.ops.example.com -n default
kubectl describe backuppolicy daily-backup -n default
```

This lab focuses on using an extended Kubernetes resource that would typically be reconciled by an Operator.

