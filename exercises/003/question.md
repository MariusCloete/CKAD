# ⚙️ Create a Kubernetes Deployment for a stateless application

Create a Kubernetes Deployment for a stateless application named `my-app` with the following requirements:
- The application should use the `nginx:1.21` image.
- It should have 3 replicas.
- Expose the application on port 80.
- Add a readiness probe to check the `/healthz` endpoint on port 80.

Provide the YAML manifest for the Deployment.