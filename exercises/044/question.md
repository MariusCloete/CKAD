# Question 44: Add startup and readiness probes for a slow-starting container

Create a Pod named `slow-start-pod` with these requirements:

- Use image `busybox:1.36`.
- Run command `sh -c "sleep 15 && touch /tmp/started && touch /tmp/ready && sleep 3600"`.
- Add a `startupProbe` that checks for file `/tmp/started`.
- Add a `readinessProbe` that checks for file `/tmp/ready`.
- Use `exec` probes.

Save the manifest as `pod.yaml` and apply it.

