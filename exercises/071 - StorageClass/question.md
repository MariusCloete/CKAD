# Question 71: Create a StorageClass and link it to a Pod

Create a storage setup for an application that requires persistent data:

- Create a `StorageClass` named `fast-storage` with:
  - `provisioner: kubernetes.io/no-provisioner` (for local/manual provisioning)
  - `volumeBindingMode: WaitForFirstConsumer`
  - `allowVolumeExpansion: true`

- Create a `PersistentVolumeClaim (PVC)` named `app-data-pvc` that:
  - References the `fast-storage` StorageClass
  - Requests `2Gi` of storage
  - Uses `ReadWriteOnce` access mode

- Create a Deployment named `data-app` that:
  - Uses image `nginx:1.27`
  - Has `1` replica
  - Mounts the PVC at path `/data`
  - Labels: `app=data-app`

Save manifests as `storageclass.yaml`, `pvc.yaml`, and `deployment.yaml`, then apply them.

Verify with:
```bash
kubectl get storageclass
kubectl get pvc
kubectl get pods -o wide
kubectl exec <pod-name> -- ls -la /data
```

