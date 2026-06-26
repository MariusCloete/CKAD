# Answer - Question 12: Create and use a Secret

## Step 1: Create the Secret (Imperative)

```bash
kubectl create secret generic app-secret \
  --from-literal=database_url=postgres://localhost:5432/mydb \
  --from-literal=api_key=secret-api-key-123 \
  --dry-run=client -o yaml > secret.yaml
```

## Step 2: Generate Pod Imperatively

```bash
kubectl run secret-consumer --image=nginx:latest --dry-run=client -o yaml > pod.yaml
```

## Step 3: Edit Pod to Add Secret References

Edit `pod.yaml` to add environment variables from the secret:

```bash
kubectl edit -f pod.yaml
```

Or manually edit the file to look like:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: secret-consumer
  labels:
    app: secret-app
spec:
  containers:
  - name: secret-consumer
    image: nginx:latest
    env:
    - name: DB_URL
      valueFrom:
        secretKeyRef:
          name: app-secret
          key: database_url
    - name: API_KEY
      valueFrom:
        secretKeyRef:
          name: app-secret
          key: api_key
```

## Step 4: Apply Resources

```bash
kubectl apply -f secret.yaml
kubectl apply -f pod.yaml
```

## Step 5: Verify

```bash
# Check secret created
kubectl get secret app-secret

# Check pod running
kubectl get pods secret-consumer

# View environment variables in pod
kubectl exec secret-consumer -- env | grep -E "DB_URL|API_KEY"

# View pod logs
kubectl logs secret-consumer
```

Expected output:
```
DB: postgres://localhost:5432/mydb
API: secret-api-key-123
```
