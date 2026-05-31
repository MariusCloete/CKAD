# Question 41: Migrate a deprecated Ingress API

Create an `Ingress` named `web-ingress` for a Service named `web-svc` with these requirements:

- Use host `web.example.com`.
- Route path `/` to Service `web-svc` port `80`.
- Use the current supported Ingress API version.
- Include `pathType`.

Save the manifest as `ingress.yaml` and apply it.

