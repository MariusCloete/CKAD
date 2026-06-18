# Question 56: Configure namespace quotas and defaults

Create resource policy objects in a namespace named `team-a` with these requirements:

- Create a `Namespace` named `team-a`
- Create a `LimitRange` name `default-limits` that sets default CPU to `200m` and default memory to `256Mi`
- Create a `ResourceQuota` name `team-a-quota`that limits the namespace to:
  - `pods: 5`
  - `requests.cpu: 1`
  - `requests.memory: 1Gi`

Save the manifests as `namespace.yaml`, `limitrange.yaml`, and `resourcequota.yaml`, then apply them.

