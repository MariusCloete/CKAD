# Question 23: Use a Deployment for a scalable web app

Create a workload for a web app with these requirements:

- Use a `Deployment` named `web-deploy`.
- Use image `nginx:1.27`.
- Run `3` replicas.
- Label Pods with `app=web`.
- Expose it with a `Service` named `web-svc` on port `80`.

Save manifests as `deployment.yaml` and `service.yaml`, then apply them.

