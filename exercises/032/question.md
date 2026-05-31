# Question 32: Configure a rolling update strategy

Create a `Deployment` named `web-rollout` with these requirements:

- Use image `nginx:1.27`.
- Run `4` replicas.
- Configure rolling updates with `maxUnavailable=0` and `maxSurge=1`.

After applying the manifest, update the image to `nginx:1.27.1` and verify rollout status.
Save your manifest as `deployment.yaml`.

