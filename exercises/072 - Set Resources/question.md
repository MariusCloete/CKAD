# Question 72: Update Deployment Resource Limits with kubectl set resources

Update resource limits on a Deployment using `kubectl set resources`:

- Create a Deployment named `web-app` with:
  - Image `nginx:1.27`
  - `2` replicas
  - Save as `deployment.yaml`

- Use `kubectl set resources` to update the container limits:
  - CPU limit: `500m`
  - Memory limit: `128Mi`
  - Use `--local --filename=deployment.yaml` to preview changes before applying
  - Output the result as YAML with `-o yaml`

- Apply the updated configuration to the cluster

- Verify the resource limits were applied:
  ```bash
  kubectl get deployment web-app -o yaml | grep -A 10 resources:
  kubectl describe deployment web-app
  ```

**Bonus**: Also set resource **requests** with:
- CPU request: `100m`
- Memory request: `64Mi`


