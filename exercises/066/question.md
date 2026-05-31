# Question 66: Troubleshoot missing endpoints caused by Pod labels

A Service should target Pods for an application named `label-demo`, but the Pods use the wrong label.

Create these resources:

- A broken `Deployment` named `label-demo` whose Pods use label `app=wrong`
- A `Service` named `label-demo-svc` selecting `app=label-demo`

Then fix the Deployment so the Service gets endpoints.

Save the manifests as `deployment-broken.yaml`, `deployment.yaml`, and `service.yaml`.

