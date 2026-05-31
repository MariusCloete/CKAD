# Question 60: Harden a Pod with securityContext and dropped capabilities

Create a Pod named `secure-pod` with these requirements:

- Use image `nginx:1.27`
- Run as user `101`
- Set `runAsNonRoot: true`
- Set `readOnlyRootFilesystem: true`
- Set `allowPrivilegeEscalation: false`
- Drop all Linux capabilities
- Add capability `NET_BIND_SERVICE`

Save the manifest as `pod.yaml` and apply it.

