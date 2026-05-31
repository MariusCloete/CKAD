# Question 39: Use Kustomize overlays for dev and prod

Create a Kustomize layout with a base and two overlays:

- Base contains a Deployment named `web` with image `nginx:1.27` and `2` replicas.
- Overlay `dev` sets replicas to `1`, adds `namePrefix: dev-`.
- Overlay `prod` sets replicas to `4`, adds `namePrefix: prod-`.

Use files under `base/` and `overlays/` and apply each overlay with `kubectl apply -k`.

