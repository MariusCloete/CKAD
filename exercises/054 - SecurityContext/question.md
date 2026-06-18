# Question 54: Use admission control with Pod Security labels

Create a namespace named `secure-apps` with Pod Security Admission labels that enforce the `restricted` profile.

Then create a Pod `secure-nginx` manifest named `pod.yaml` in that namespace that:

- Uses image `nginx:1.27`
- Runs as non-root
- Disables privilege escalation

Save the manifests as `namespace.yaml` and `pod.yaml`, then apply them.

 