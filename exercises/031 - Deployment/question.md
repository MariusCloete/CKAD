# Question 31: Create a Deployment and expose it

Create an application deployment with these requirements:

- Use a `Deployment` named `api-deploy`.
- Use image `nginx:1.27`.
- Run `3` replicas.
- Label Pods with `app=api` and `tier=backend`.
- Expose it with a `Service` named `api-svc` on port `80`.

Save manifests as `deployment.yaml` and `service.yaml`, then apply them.

