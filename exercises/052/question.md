# Question 52: Create an operator-managed custom resource

Assume a cluster already contains a CRD for `BackupPolicy` in API group `ops.example.com/v1`.

Create a custom resource with these requirements:

- Kind: `BackupPolicy`
- Name: `daily-backup`
- Namespace: `default`
- `spec.schedule`: `0 1 * * *`
- `spec.retentionDays`: `7`
- `spec.targetRef.name`: `orders-db`

Save the manifest as `backuppolicy.yaml` and apply it.

