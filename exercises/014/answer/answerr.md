1. **What is a ConfigMap?**
   - A ConfigMap is used to store non-sensitive configuration data in key-value pairs. Unlike Secrets, ConfigMaps are not encrypted and are used for general configuration.

2. **Example**:
   - Create a ConfigMap:
     ```bash
     kubectl create configmap my-config --from-literal=app.name=myapp --from-literal=app.version=1.0
     ```

   - Use the ConfigMap in a Pod:
     - see file `pod.yaml`