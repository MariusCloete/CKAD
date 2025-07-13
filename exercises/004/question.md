# ⚙️ Create a Kubernetes ConfigMap and Pod

Create a ConfigMap named `app-config` with the following key-value pairs:
- `APP_ENV=production`
- `APP_DEBUG=false`

Then, create a Pod named `app-pod` that uses the `busybox` image and mounts the `APP_ENV` and `APP_DEBUG` values as environment variables.

Provide the YAML manifests for both the ConfigMap and the Pod.