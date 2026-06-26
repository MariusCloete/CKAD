# Question 64: Troubleshoot a Service with a wrong selector

A Service should route traffic to a Deployment, but it has the wrong selector.

Create these resources:

- A `Deployment` named `selector-demo` with label `app=selector-demo`
- A broken `Service` named `selector-demo-svc` that currently selects `app=wrong-label`

Then fix the Service so it correctly routes traffic to the Pods.

Save the manifests as `deployment.yaml`, `service-broken.yaml`, and `service.yaml`.

