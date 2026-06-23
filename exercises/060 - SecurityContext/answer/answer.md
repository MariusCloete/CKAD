Apply the Pod manifest:

```bash
kubectl run secure-pod --image=nginx:1.27 --dry-run=client -o yaml  > pod.yaml
```
Add the following the root spec of the Pod manifest:

```yaml
securityContext:
  runAsUser: 101
  runAsNonRoot: true
  readOnlyRootFilesystem: true
  allowPrivilegeEscalation: false
  capabilities:
    drop:
      - ALL
    add:
      - NET_BIND_SERVICE  
```      
```bash
kubectl apply -f pod.yaml
kubectl get pod secure-pod
kubectl describe pod secure-pod
```

