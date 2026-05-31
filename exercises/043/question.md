# Question 43: Add liveness and readiness probes

Create a Pod named `probe-pod` with these requirements:

- Use image `nginx:1.27`.
- Expose container port `80`.
- Add an HTTP `livenessProbe` on path `/` and port `80`.
- Add an HTTP `readinessProbe` on path `/` and port `80`.
- Use `initialDelaySeconds: 5` and `periodSeconds: 10` for both probes.

Save the manifest as `pod.yaml` and apply it.

