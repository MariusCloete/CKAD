# Question 62: Expose an application with a NodePort Service

Create a workload with these requirements:

- Create a `Deployment` named `web-nodeport` using image `nginx:1.27`
- Run `2` replicas
- Label Pods with `app=web-nodeport`
- Create a `Service` named `web-nodeport-svc`
- Service type must be `NodePort`
- Expose service port `80` to container port `80`
- Use nodePort `30080`

Save the manifests as `deployment.yaml` and `service.yaml`, then apply them.

