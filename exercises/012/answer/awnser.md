1. **What are Kubernetes Secrets?**
    - Kubernetes Secrets are used to store sensitive information, such as passwords, tokens, or keys, securely. They help avoid exposing sensitive data in Pod specifications.

2. **Example**:
    - Create a Secret:
      ```bash
      kubectl create secret generic my-secret --from-literal=username=admin --from-literal=password=secret123
      ```

    - Use the Secret in a Pod:
      - see file pod.yaml