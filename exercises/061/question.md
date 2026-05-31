# Question 61: Expose an application with a ClusterIP Service

Create a workload with these requirements:

- Create a `Deployment` named `web-clusterip` using image `nginx:1.27`
- Run `2` replicas
- Label Pods with `app=web-clusterip`
- Create a `Service` named `web-clusterip-svc`
- Service type must be `ClusterIP`
- Expose port `80` to container port `80`

Save the manifests as `deployment.yaml` and `service.yaml`, then apply them.

