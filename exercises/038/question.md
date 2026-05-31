# Question 38: Build and apply a Kustomize base

Create a Kustomize base for an app named `kustom-web`:

- Deployment with image `nginx:1.27` and `2` replicas.
- Service named `kustom-web` on port `80`.
- Use `kustomization.yaml` to include resources.

Apply using `kubectl apply -k .` from the directory containing the kustomization file.

