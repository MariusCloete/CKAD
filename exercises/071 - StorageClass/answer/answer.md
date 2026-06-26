# Answer - Question 71: Create a StorageClass and link it to a Pod

## Step 1: Create the StorageClass

```bash
kubectl apply -f storageclass.yaml
```

Verify:
```bash
kubectl get storageclass
kubectl describe storageclass fast-storage
```

## Step 2: Create the PersistentVolumeClaim

```bash
kubectl apply -f pvc.yaml
```

Verify:
```bash
kubectl get pvc app-data-pvc
kubectl describe pvc app-data-pvc
```

## Step 3: Create the Deployment

```bash
kubectl apply -f deployment.yaml
```

Verify:
```bash
kubectl get deployment data-app
kubectl get pods -l app=data-app -o wide
```

## Step 4: Verify the volume is mounted

```bash
# Get pod name
POD_NAME=$(kubectl get pods -l app=data-app -o jsonpath='{.items[0].metadata.name}')

# Check mounted volume
kubectl exec $POD_NAME -- ls -la /data

# Try creating a file
kubectl exec $POD_NAME -- sh -c "echo 'test data' > /data/test.txt"

# Verify file persists
kubectl exec $POD_NAME -- cat /data/test.txt
```

## Imperative Approach (Alternative)

```bash
# Create StorageClass (imperative)
kubectl create storageclass fast-storage \
  --provisioner=kubernetes.io/no-provisioner \
  --dry-run=client -o yaml | kubectl apply -f -

# Create PVC (imperative)
kubectl create pvc app-data-pvc \
  --storageclass=fast-storage \
  --size=2Gi \
  --access-modes=ReadWriteOnce \
  --dry-run=client -o yaml | kubectl apply -f -

# Create Deployment with volume mount
kubectl create deployment data-app \
  --image=nginx:1.27 \
  --replicas=1 \
  --dry-run=client -o yaml > deployment.yaml

# Then edit deployment.yaml to add volumeMounts and volumes
```

## Key Concepts

- **StorageClass**: Defines storage provisioning parameters
- **volumeBindingMode: WaitForFirstConsumer**: Delays binding PVC to PV until pod scheduling
- **allowVolumeExpansion: true**: Allows resizing PVC after creation
- **PVC to Pod link**: Reference PVC in pod spec via `persistentVolumeClaim.claimName`
- **volumeMounts**: Container-level mount point
- **volumes**: Pod-level volume definition

