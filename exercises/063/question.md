# Question 63: Expose an application on a custom target port

Create a workload with these requirements:

- Create a `Deployment` named `api-service-demo`
- Use image `hashicorp/http-echo:1.0`
- Run command `-text=hello`
- Expose container port `5678`
- Label Pods with `app=api-service-demo`
- Create a `Service` named `api-service-demo-svc`
- Expose service port `80` and forward traffic to container port `5678`

Save the manifests as `deployment.yaml` and `service.yaml`, then apply them.

