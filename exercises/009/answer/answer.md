
To add a liveness probe to a Pod running the nginx:latest image, use the following YAML configuration:
```yaml
livenessProbe:
  httpGet:
    path: /healthz
    port: 8080
  initialDelaySeconds: 10
  periodSeconds: 10
```
Explanation:
httpGet: Specifies the HTTP endpoint to check.
path: The endpoint to probe (/healthz).
port: The port to use (8080).
initialDelaySeconds: Time to wait before the first probe.
periodSeconds: Interval between probes.