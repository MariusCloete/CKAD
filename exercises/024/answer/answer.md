Apply the DaemonSet:

```bash
kubectl apply -f daemonset.yaml
kubectl -n kube-system get ds node-agent
kubectl -n kube-system get pods -l app=node-agent -o wide
```

