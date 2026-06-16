# Question 29: Use a PersistentVolumeClaim for durable data

Create a workload with persistent storage:

- Create a `PersistentVolumeClaim` named `web-data-pvc` requesting `1Gi`.
- Access mode must be `ReadWriteOnce`.
- Create a `Deployment` named `web-data-deploy` with image `nginx:1.27`.
- Mount the PVC at `/usr/share/nginx/html`.

Save manifests as `pvc.yaml` and `deployment.yaml`, then apply them.

