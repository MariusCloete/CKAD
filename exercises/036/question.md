# Question 36: Deploy an existing package with Helm

Use Helm to deploy NGINX from an existing chart:

- Add repository `bitnami` from `https://charts.bitnami.com/bitnami`.
- Install release `web` from chart `bitnami/nginx`.
- Use namespace `helm-lab` and create it if needed.
- Override values so `replicaCount=2` and Service type is `ClusterIP`.

Save your custom values in `values.yaml`.

