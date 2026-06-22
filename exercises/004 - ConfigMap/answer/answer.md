
k create configmap app-config --from-literal=APP_ENV=production --from-literal=APP_DEBUG=false --dry-run=client -o yaml > q4.yaml

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  APP_ENV: production
  APP_DEBUG: "false"
```

k run app-pod --image=busybox --dry-run=client -o yaml > q4pod.yaml

```yaml
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: app-pod
  name: app-pod
spec:
  containers:
  - image: busybox
    name: app-pod
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}
```
Under resources, you can add the environment variables from the ConfigMap like this:

```yaml
  containers:
  - image: busybox
    name: app-pod
    envFrom:
    - configMapRef:
        name: app-config
    resources: {}
```
NB: The `envFrom` field allows you to import all key-value pairs from the specified ConfigMap as environment variables in the container.
If you want to specify each environment variable individually, you can use the `env` field instead:

```yaml
  containers:
  - image: busybox
    name: app-pod
    env:
    - name: APP_ENV
      valueFrom:
        configMapKeyRef:
          name: app-config
          key: APP_ENV
    - name: APP_DEBUG
      valueFrom:
        configMapKeyRef:
          name: app-config
          key: APP_DEBUG
    resources: {}
```
