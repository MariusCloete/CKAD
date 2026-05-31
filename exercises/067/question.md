# Question 67: Create a default deny ingress NetworkPolicy

Create a networking lab in namespace `default` with these requirements:

- Create a Pod named `backend` with label `app=backend` using image `nginx:1.27`
- Create a `NetworkPolicy` named `deny-backend-ingress`
- The policy must select Pods with label `app=backend`
- Deny all incoming traffic to those Pods

Save the manifests as `pod.yaml` and `networkpolicy.yaml`, then apply them.

