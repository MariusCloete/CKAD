# Question 73: Configure RBAC with ServiceAccount, Role, and RoleBinding

Create a RBAC setup for an application that needs read-only access to pods:

- Create a namespace named `app-namespace`

- Create a ServiceAccount named `app-reader` in the namespace

- Create a Role named `pod-reader` that allows:
  - `get` pods
  - `list` pods
  - `watch` pods
  - In the same namespace (`app-namespace`)

- Create a RoleBinding named `read-pods` that:
  - Binds the `pod-reader` Role to the `app-reader` ServiceAccount
  - In the same namespace (`app-namespace`)

- Verify the RBAC configuration:
  ```bash
  kubectl get serviceaccount -n app-namespace
  kubectl get role -n app-namespace
  kubectl get rolebinding -n app-namespace
  kubectl auth can-i list pods --as=system:serviceaccount:app-namespace:app-reader -n app-namespace
  kubectl auth can-i delete pods --as=system:serviceaccount:app-namespace:app-reader -n app-namespace
  ```

Save manifests as `namespace.yaml`, `serviceaccount.yaml`, `role.yaml`, and `rolebinding.yaml`.

**Bonus**: Create a Pod that uses the `app-reader` ServiceAccount and test if it can access pod information.

