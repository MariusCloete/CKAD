# Question 70: Expose two applications with path-based Ingress routing

Create resources with these requirements:

- Create a `Deployment` named `frontend-app` using image `nginx:1.27`
- Create a `Deployment` named `api-app` using image `hashicorp/http-echo:1.0` with argument `-text=api`
- Create `Service` objects named `frontend-svc` and `api-svc`
- Create an `Ingress` named `apps-ingress`
- Route path `/` to `frontend-svc` port `80`
- Route path `/api` to `api-svc` port `80`
- Use host `apps.example.com`

Save the manifests as `frontend-deployment.yaml`, `api-deployment.yaml`, `frontend-service.yaml`, `api-service.yaml`, and `ingress.yaml`, then apply them.

