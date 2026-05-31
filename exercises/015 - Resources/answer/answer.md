1. **What are resource requests and limits?**
   - Resource requests specify the minimum resources a container needs, while limits define the maximum resources it can use. They ensure efficient resource allocation and prevent resource contention.

2. **Example**:
   ```yaml
   apiVersion: v1
   kind: Pod
   metadata:
     name: resource-pod
   spec:
     containers:
     - name: app
       image: nginx
       resources:
         requests:
           memory: "64Mi"
           cpu: "250m"
         limits:
           memory: "128Mi"
           cpu: "500m"