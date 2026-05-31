# Question 59: Use a dedicated ServiceAccount in a Pod

Create a `ServiceAccount` named `app-sa` in namespace `default`.

Then create a Pod named `sa-demo` that:

- Uses image `busybox:1.36`
- Uses `serviceAccountName: app-sa`
- Sets `automountServiceAccountToken: false`
- Runs command `sh -c "sleep 3600"`

Save the manifests as `serviceaccount.yaml` and `pod.yaml`, then apply them.

