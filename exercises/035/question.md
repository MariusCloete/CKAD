# Question 35: Implement canary deployment using two Deployments

Create a canary setup for an app named `payments`:

- Stable Deployment `payments-stable` with image `nginx:1.27` and `5` replicas.
- Canary Deployment `payments-canary` with image `nginx:1.27.1` and `1` replica.
- Both deployments must use label `app=payments`.
- Add labels `track=stable` and `track=canary` respectively.
- Create a `Service` named `payments-svc` that routes to both tracks.

Save manifests as `deploy-stable.yaml`, `deploy-canary.yaml`, and `service.yaml`.

