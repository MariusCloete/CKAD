# Question 69: Expose an application with a host-based Ingress rule

Create resources with these requirements:

- Create a `Deployment` named `ingress-web` using image `nginx:1.27`
- Label Pods with `app=ingress-web`
- Create a `Service` named `ingress-web-svc` on port `80`
- Create an `Ingress` named `ingress-web`
- Route host `app.example.com` and path `/` to `ingress-web-svc` port `80`
- Use the current supported Ingress API version and include `pathType`

Save the manifests as `deployment.yaml`, `service.yaml`, and `ingress.yaml`, then apply them.

