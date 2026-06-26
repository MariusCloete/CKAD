# Question 12: Create and use a Secret

Create a Kubernetes Secret and consume it in a Pod:

- Create an `Opaque` Secret named `app-secret` with:
  - Key `database_url` with value `postgres://localhost:5432/mydb`
  - Key `api_key` with value `secret-api-key-123`
- Create a Pod named `secret-consumer` that:
  - Uses image `busybox:1.36`
  - Consumes the secret values as environment variables `DB_URL` and `API_KEY`
  - Runs command `sh -c "echo DB: $DB_URL; echo API: $API_KEY; sleep 3600"`

Save the manifests as `secret.yaml` and `pod.yaml`, then apply them.
