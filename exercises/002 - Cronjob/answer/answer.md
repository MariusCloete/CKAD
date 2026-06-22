A:You need to use kubectl apply with a YAML manifest or use kubectl create with --dry-run and -o yaml to generate the manifest first. For example:
``` bash
kubectl create deployment web-server --image=nginx:latest --dry-run=client -o yaml > web-server.yaml
```
Then, modify the generated YAML to change the kind to DaemonSet and apply it:
``` bash
kubectl apply -f web-server.yaml
```
B:
```bash
k create cj test --image=busybox:latest --schedule="0 0 * * *" -- ""sh", "-c", "echo 'Running batch job'"" --dry-run=client -o yaml > daily-batch-job.yaml
```
Then apply it:
``` bash
kubectl apply -f daily-batch-job.yaml
```
C: You can create the deployment for scenario c using the following single-line command:
``` bash
kubectl create deployment stateless-api --image=node:18-alpine --replicas=3 --dry-run=client -o yaml | kubectl apply -f -
```
