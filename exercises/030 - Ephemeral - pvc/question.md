# Question 30: Combine persistent and ephemeral volumes

Create a `Deployment` named `notes-app` with these requirements:

- Use image `busybox:1.36`.
- Run command `sh -c "echo started >> /data/app.log && sleep 3600"`.
- Mount a PVC named `notes-pvc` at `/data` for persistent data.
- Mount an `emptyDir` volume at `/tmp/cache` for ephemeral cache.
- Create `notes-pvc` with `1Gi` and `ReadWriteOnce`.

Save manifests as `pvc.yaml` and `deployment.yaml`, then apply them.

