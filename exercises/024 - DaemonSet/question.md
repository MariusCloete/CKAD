# Question 24: Use a DaemonSet for node-level agents

Create a node-level log agent with these requirements:

- Use a `DaemonSet` named `node-agent`.
- Run one Pod on every node in namespace `kube-system`.
- Use image `busybox:1.36`.
- Run command `sh -c "sleep 3600"`.

Save the manifest as `daemonset.yaml` and apply it.

