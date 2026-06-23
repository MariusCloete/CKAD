Apply both manifests:

```bash
kubectl create deployment web-clusterip --image=nginx:1.27 --replicas=2 --dry-run=client -o yaml > deployment.yaml
kubectl apply -f deployment.yaml
```
```bash
kubectl expose deployment web-clusterip --type=ClusterIp --port=80 --target-port=80 --dry-run=client -o yaml > service.yaml
kubectl apply -f service.yaml
```
```bash
kubectl get deploy web-clusterip
kubectl get svc web-clusterip-svc
kubectl get endpoints web-clusterip-svc
```

