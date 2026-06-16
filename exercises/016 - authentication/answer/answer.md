1. **What is a Custom Resource Definition (CRD) in Kubernetes, and how does it extend Kubernetes functionality?**  
   - A CRD is a way to define custom resources in Kubernetes. It allows users to extend Kubernetes by creating their own resource types, which behave like built-in Kubernetes resources. CRDs enable the Kubernetes API to manage these custom resources.

2. **What is an Operator in Kubernetes, and how does it relate to CRDs?**  
   - An Operator is a method of packaging, deploying, and managing a Kubernetes application. It uses CRDs to define the application's desired state and includes logic to automate tasks like scaling, backups, and updates. Operators extend Kubernetes functionality by managing complex applications.

3. **Explain the difference between authentication and authorization in Kubernetes.**  
   - **Authentication** verifies the identity of a user or service (e.g., using certificates, tokens, or ServiceAccounts).  
   - **Authorization** determines what actions the authenticated user or service is allowed to perform (e.g., using Role-Based Access Control (RBAC)).

4. **Example of configuring Kubernetes authentication using a ServiceAccount**:  
   A **ServiceAccount** in Kubernetes is a resource used to provide an identity for processes running in a Pod. It allows Pods to authenticate with the Kubernetes API and interact with cluster resources securely. By default, every Pod is associated with the `default` ServiceAccount in its namespace unless explicitly specified.

### Key Features of ServiceAccounts:
1. **Authentication**: ServiceAccounts authenticate Pods to the Kubernetes API using tokens.
2. **Authorization**: Combined with Role-Based Access Control (RBAC), ServiceAccounts define what actions a Pod can perform.
3. **Isolation**: You can create separate ServiceAccounts for different Pods to limit their access to cluster resources.

### Components of a ServiceAccount:
- **ServiceAccount Resource**: Defines the account.
- **Token Secret**: Automatically created and mounted into Pods to authenticate with the API.

### Example:
1. **Create a ServiceAccount**:
   ```yaml
   apiVersion: v1
   kind: ServiceAccount
   metadata:
     name: my-service-account
   ```

2. **Assign the ServiceAccount to a Pod**:
   ```yaml
   apiVersion: v1
   kind: Pod
   metadata:
     name: example-pod
   spec:
     serviceAccountName: my-service-account
     containers:
       - name: app
         image: nginx
   ```

3. **RBAC Example** (Granting permissions):
   ```yaml
   apiVersion: rbac.authorization.k8s.io/v1
   kind: Role
   metadata:
     namespace: default
     name: pod-reader
   rules:
     - apiGroups: [""]
       resources: ["pods"]
       verbs: ["get", "list"]

   ---
   apiVersion: rbac.authorization.k8s.io/v1
   kind: RoleBinding
   metadata:
     name: pod-reader-binding
     namespace: default
   subjects:
     - kind: ServiceAccount
       name: my-service-account
       namespace: default
   roleRef:
     kind: Role
     name: pod-reader
     apiGroup: rbac.authorization.k8s.io
   ```

### How It Works:
- The ServiceAccount token is mounted into the Pod at `/var/run/secrets/kubernetes.io/serviceaccount`.
- The Pod uses this token to authenticate with the Kubernetes API.
- RBAC rules determine what the ServiceAccount can do.