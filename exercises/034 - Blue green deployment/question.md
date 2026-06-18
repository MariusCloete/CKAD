# Question 34: Implement blue/green deployment

Create a blue/green setup for an app named `shop`:

- Create `Deployment` `shop-blue` with label `version=blue` and image `nginx:1.27`.
- Create `Deployment` `shop-green` with label `version=green` and image `nginx:1.27.1`.
- Both deployments must use label `app=shop` and `2` replicas.
- Create a `Service` named `shop-svc` that initially routes traffic to blue.
- Show how to switch traffic to green.

Save manifests as `deploy-blue.yaml`, `deploy-green.yaml`, and `service.yaml`.

