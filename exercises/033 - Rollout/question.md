# Question 33: Perform a controlled rollout and rollback

Create a `Deployment` named `checkout` with these requirements:

- Use image `nginx:1.27`.
- Run `3` replicas.

Then do the following:

- Pause the rollout.
- Change image to `nginx:1.27.1`.
- Resume the rollout.
- Roll back to the previous revision.

Save your manifest as `deployment.yaml`.

