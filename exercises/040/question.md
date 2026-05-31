# Question 40: Use Kustomize to patch image and labels

Create a Kustomize base + overlay setup:

- Base has a Deployment named `frontend` with image `nginx:1.27` and label `app=frontend`.
- Overlay `staging` must:
  - change image tag to `nginx:1.27.1`
  - add label `env=staging` to all resources
  - add annotation `owner=platform-team` to the Deployment

Use `base/` and `overlays/staging/` directories and apply with `kubectl apply -k overlays/staging`.

