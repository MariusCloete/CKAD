# Question 53: Grant Pod read access with RBAC

Create RBAC objects with these requirements:

- Create a `ServiceAccount` named `pod-reader` in namespace `default`.
- Create a `Role` named `pod-reader-role` that can `get`, `list`, and `watch` `pods`.
- Create a `RoleBinding` named `pod-reader-binding` that binds the Role to the ServiceAccount.

Save the manifests as `serviceaccount.yaml`, `role.yaml`, and `rolebinding.yaml`, then apply them.

