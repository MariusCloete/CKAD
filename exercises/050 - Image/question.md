# Question 50: Debug a failing Deployment rollout

Create a `Deployment` named `bad-web` with these requirements:

- Use image `nginx:9.99`.
- Run `2` replicas.
- Label Pods with `app=bad-web`.

Apply the manifest, inspect why the rollout fails, then fix it by updating the image to `nginx:1.27`.
Save the manifest as `deployment.yaml`.

