# Question 58: Create and consume a Secret

Create an `Opaque` Secret named `db-secret` with these requirements:

- Key `username` with value `appuser`
- Key `password` with value `s3cr3t`

Then create a Pod named `secret-demo` that:

- Uses image `busybox:1.36`
- Consumes `username` and `password` as environment variables `DB_USER` and `DB_PASSWORD`
- Runs command `sh -c "echo $DB_USER; echo $DB_PASSWORD; sleep 3600"`

Save the manifests as `secret.yaml` and `pod.yaml`, then apply them.

