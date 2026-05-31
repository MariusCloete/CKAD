# Question 65: Troubleshoot a Service with the wrong targetPort

A Service exists, but it points to the wrong container port.

Create these resources:

- A `Deployment` named `port-demo` with label `app=port-demo`
- Container image `hashicorp/http-echo:1.0`
- Container port `5678`
- A broken `Service` named `port-demo-svc` with `targetPort: 8080`

Then fix the Service so it correctly forwards traffic.

Save the manifests as `deployment.yaml`, `service-broken.yaml`, and `service.yaml`.

