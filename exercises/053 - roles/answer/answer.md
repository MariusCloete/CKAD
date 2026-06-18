Apply all manifests:
```bash
k create role pod-reader-role --verb=get,list,watch --resource=pod --dry-run=client -o yaml > role.yaml
````
```bash
k create rolebinding pod-reader-binding --role=pod-reader-role --serviceaccount=default:pod-reader --dry-run=client -o yaml > rolebinding.yaml

```
```bash
kubectl apply -f serviceaccount.yaml
kubectl apply -f role.yaml
kubectl apply -f rolebinding.yaml
kubectl auth can-i list pods --as=system:serviceaccount:default:pod-reader -n default
```

This lab focuses on Kubernetes authorization with RBAC.

