# Question 68: Allow ingress to a backend only from frontend Pods

Create a networking lab with these requirements:

- Create a Pod named `frontend` with label `app=frontend` using image `busybox:1.36`
- Create a Pod named `backend` with label `app=backend` using image `nginx:1.27`
- Create a `NetworkPolicy` named `allow-frontend-to-backend`
- The policy must allow ingress to Pods labeled `app=backend` only from Pods labeled `app=frontend`
- Allow TCP traffic on port `80`

Save the manifests as `frontend.yaml`, `backend.yaml`, and `networkpolicy.yaml`, then apply them.

