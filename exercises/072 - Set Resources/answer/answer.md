# Answer - Question 72: Update Deployment Resource Limits with kubectl set resources

## Step 1: Create the initial Deployment

```bash
kubectl apply -f deployment.yaml
```

## Step 2: Preview resource limit changes locally

Use `kubectl set resources` with `--local` flag to preview changes:

```bash
kubectl set resources deployment web-app \
  --limits=cpu=500m,memory=128Mi \
  --filename=deployment.yaml \
  --local -o yaml
```

**Important**: When using `--local`, you MUST specify the filename with `-f` or `--filename`.

**Output**: Shows the deployment YAML with resource limits added (doesn't apply to cluster).

## Step 3: Apply resource limits to the cluster

```bash
kubectl set resources deployment web-app \
  --limits=cpu=500m,memory=128Mi
```

Or pipe the local output and apply:

```bash
kubectl set resources deployment web-app \
  --limits=cpu=500m,memory=128Mi \
  --filename=deployment.yaml \
  --local -o yaml | kubectl apply -f -
```

## Step 4: Set resource requests (Bonus)

```bash
kubectl set resources deployment web-app \
  --requests=cpu=100m,memory=64Mi
```

Or set both limits and requests together:

```bash
kubectl set resources deployment web-app \
  --limits=cpu=500m,memory=128Mi \
  --requests=cpu=100m,memory=64Mi
```

## Step 5: Verify the changes

```bash
# View full deployment YAML
kubectl get deployment web-app -o yaml

# View just the resources section
kubectl get deployment web-app -o yaml | grep -A 15 "resources:"

# Describe the deployment
kubectl describe deployment web-app

# Check running pods
kubectl get pods -l app=web-app -o wide
```

## Expected Output Structure

```yaml
spec:
  template:
    spec:
      containers:
      - name: nginx
        image: nginx:1.27
        resources:
          limits:
            cpu: 500m
            memory: 128Mi
          requests:
            cpu: 100m
            memory: 64Mi
```

## Key Concepts

- **`kubectl set resources`**: Updates CPU and memory limits/requests on deployments
- **`--limits`**: Set container resource upper limits
- **`--requests`**: Set guaranteed minimum resources
- **`--local`**: Preview changes without applying to cluster
- **`-o yaml`**: Output result as YAML (doesn't apply with `--local`)
- **CPU units**: `m` = millicores (1000m = 1 CPU)
- **Memory units**: `Mi` = Mebibytes, `Gi` = Gibibytes

## Command Syntax

```bash
# With --local (requires --filename)
kubectl set resources <resource-type> <resource-name> \
  [--limits=cpu=<value>,memory=<value>] \
  [--requests=cpu=<value>,memory=<value>] \
  --filename=<filepath> \
  --local \
  [-o yaml]

# Without --local (applies to cluster)
kubectl set resources <resource-type> <resource-name> \
  [--limits=cpu=<value>,memory=<value>] \
  [--requests=cpu=<value>,memory=<value>]
```

## Common Flags

| Flag                  | Purpose |
|-----------------------|---------|
| `--limits`            | Set resource upper limits |
| `--requests`          | Set guaranteed minimum resources |
| `--filename` / `-f`   | Source file (REQUIRED when using `--local`) |
| `--local`             | Preview only (don't apply to cluster) |
| `-o yaml`             | Output as YAML (useful with `--local`) |
| `--containers` / `-c` | Target specific containers |
| `--all`               | Update all resources in namespace |

## Real-World Notes

- **Requests**: Kubernetes scheduler uses this to place pods on nodes
- **Limits**: Container is throttled/killed if exceeded
- **Always set both**: Requests for scheduling, limits for pod security
- **Use `--local` with `--filename`**: When previewing with `--local`, you MUST provide the source file with `-f` or `--filename`
- **Common Error**: Forgetting `--filename` when using `--local` results in: "you must specify resources by --filename when --local is set"

