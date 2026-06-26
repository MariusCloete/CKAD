# Answer - Question 73: Configure RBAC with ServiceAccount, Role, and RoleBinding

## Imperative Method (Quick & Easy)

### Step 1: Create the namespace

```bash
kubectl create namespace app-namespace
```

Verify:
```bash
kubectl get namespace app-namespace
```

### Step 2: Create the ServiceAccount

```bash
kubectl create serviceaccount app-reader -n app-namespace
```

Verify:
```bash
kubectl get serviceaccount -n app-namespace
kubectl describe serviceaccount app-reader -n app-namespace
```

### Step 3: Create the Role

```bash
kubectl create role pod-reader -n app-namespace \
  --verb=get,list,watch \
  --resource=pods
```

Verify:
```bash
kubectl get role -n app-namespace
kubectl describe role pod-reader -n app-namespace
```

The Role defines permissions:
- `--verb=get,list,watch` = Allowed operations
- `--resource=pods` = Pod objects
- `-n app-namespace` = Namespace-scoped

### Step 4: Create the RoleBinding

```bash
kubectl create rolebinding read-pods -n app-namespace \
  --role=pod-reader \
  --serviceaccount=app-namespace:app-reader
```

Verify:
```bash
kubectl get rolebinding -n app-namespace
kubectl describe rolebinding read-pods -n app-namespace
```

### Complete One-Liner Workflow

```bash
# Create all RBAC resources in sequence
kubectl create namespace app-namespace && \
kubectl create serviceaccount app-reader -n app-namespace && \
kubectl create role pod-reader -n app-namespace --verb=get,list,watch --resource=pods && \
kubectl create rolebinding read-pods -n app-namespace --role=pod-reader --serviceaccount=app-namespace:app-reader
```

---

## Declarative Method (Alternative)

### Step 1: Create the namespace

```bash
kubectl apply -f namespace.yaml
```

### Step 2: Create the ServiceAccount

```bash
kubectl apply -f serviceaccount.yaml
```

### Step 3: Create the Role

```bash
kubectl apply -f role.yaml
```

### Step 4: Create the RoleBinding

```bash
kubectl apply -f rolebinding.yaml
```

## Step 5: Test RBAC permissions

### Test what the ServiceAccount CAN do (Allowed):

```bash
# Can list pods? (Should be allowed)
kubectl auth can-i list pods \
  --as=system:serviceaccount:app-namespace:app-reader \
  -n app-namespace

# Output: yes
```

```bash
# Can get pods? (Should be allowed)
kubectl auth can-i get pods \
  --as=system:serviceaccount:app-namespace:app-reader \
  -n app-namespace

# Output: yes
```

```bash
# Can watch pods? (Should be allowed)
kubectl auth can-i watch pods \
  --as=system:serviceaccount:app-namespace:app-reader \
  -n app-namespace

# Output: yes
```

### Test what the ServiceAccount CANNOT do:

```bash
# Can delete pods? (Should be denied)
kubectl auth can-i delete pods \
  --as=system:serviceaccount:app-namespace:app-reader \
  -n app-namespace

# Output: no
```

```bash
# Can create pods? (Should be denied)
kubectl auth can-i create pods \
  --as=system:serviceaccount:app-namespace:app-reader \
  -n app-namespace

# Output: no
```

## Bonus: Create a Pod using the ServiceAccount

### Declarative Method:

```bash
kubectl apply -f pod-bonus.yaml
```

### Imperative Method (Create then set serviceaccount):

```bash
# Step 1: Create pod
kubectl run app-pod \
  -n app-namespace \
  --image=busybox:1.36 \
  --dry-run=client -o yaml  \
  --command  \
  -- "sleep" "3600"  > pod-bonus.yaml
```

**Note:** `--serviceaccount` flag is NOT available in `kubectl run`. Use `kubectl set serviceaccount` instead.

```bash
# Step 2: Update the pod's serviceaccount
kubectl set serviceaccount pod app-pod \
  -n app-namespace \
  --serviceaccount=app-reader
```

### Verify the pod is running:

```bash
kubectl get pods -n app-namespace
kubectl describe pod app-pod -n app-namespace
```

### Check the ServiceAccount mounted in the pod:

```bash
kubectl exec app-pod -n app-namespace -- cat /var/run/secrets/kubernetes.io/serviceaccount/namespace
kubectl exec app-pod -n app-namespace -- ls -la /var/run/secrets/kubernetes.io/serviceaccount/
```

## RBAC Components Explained

| Component | Purpose | Example |
|-----------|---------|---------|
| **ServiceAccount** | Identity for pods/users | `app-reader` |
| **Role** | Defines permissions for resources | `pod-reader` (get/list/watch pods) |
| **RoleBinding** | Connects Role to ServiceAccount | Binds `pod-reader` to `app-reader` |

## Complete Imperative Workflow (All-in-One)

```bash
# Create all RBAC resources
kubectl create namespace app-namespace && \
kubectl create serviceaccount app-reader -n app-namespace && \
kubectl create role pod-reader -n app-namespace --verb=get,list,watch --resource=pods && \
kubectl create rolebinding read-pods -n app-namespace --role=pod-reader --serviceaccount=app-namespace:app-reader

# Quick verification of all RBAC resources
kubectl get serviceaccount,role,rolebinding -n app-namespace

# Test permissions (allowed operations)
kubectl auth can-i list pods --as=system:serviceaccount:app-namespace:app-reader -n app-namespace
kubectl auth can-i get pods --as=system:serviceaccount:app-namespace:app-reader -n app-namespace
kubectl auth can-i watch pods --as=system:serviceaccount:app-namespace:app-reader -n app-namespace

# Test permissions (denied operations)
kubectl auth can-i delete pods --as=system:serviceaccount:app-namespace:app-reader -n app-namespace
kubectl auth can-i create pods --as=system:serviceaccount:app-namespace:app-reader -n app-namespace

# Optional: Create test pod with serviceaccount
kubectl run test-pod -n app-namespace --image=busybox:1.36 --command sleep 3600
kubectl set serviceaccount pod test-pod -n app-namespace --serviceaccount=app-reader
kubectl exec test-pod -n app-namespace -- ls /var/run/secrets/kubernetes.io/serviceaccount/
```

## Key Concepts

- **apiGroups**: "" = core API, "apps" = apps API, "batch" = batch API
- **resources**: pods, deployments, services, etc.
- **verbs**: get, list, watch, create, update, patch, delete, etc.
- **Kind: Role**: Namespace-scoped permissions
- **Kind: ClusterRole**: Cluster-wide permissions (use ClusterRoleBinding)
- **subjects**: Who the permissions apply to (ServiceAccount, User, Group)
- **@**: Indicates a token from a ServiceAccount

## Common RBAC Mistakes

| Mistake | Problem | Fix |
|---------|---------|-----|
| Wrong namespace in RoleBinding | Permissions don't apply | Match namespace in Role, RoleBinding, ServiceAccount |
| Forgot `apiGroup` in Rule | Resource not found | Set to "" for core API, "apps" for apps, etc. |
| Used Role instead of ClusterRole | Can't grant cluster-wide access | Use ClusterRole for cluster-wide, Role for namespace-scoped |
| Wrong subject name | Binding doesn't match | Use exact ServiceAccount name |

## Testing Permissions

```bash
# Check if a user/SA can perform an action
kubectl auth can-i <verb> <resource> --as=<user-or-sa>

# Examples:
kubectl auth can-i list pods --as=user@example.com
kubectl auth can-i delete configmaps --as=system:serviceaccount:default:my-sa
```


