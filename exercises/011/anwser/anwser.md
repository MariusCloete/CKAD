1. **How Taints and Tolerations Work**:
    - **Taints**: Applied to nodes to repel Pods that do not have matching tolerations. A taint consists of a key, value, and effect (`NoSchedule`, `PreferNoSchedule`, or `NoExecute`).
    - **Tolerations**: Added to Pods to allow them to be scheduled on nodes with matching taints. A toleration must match the key, value, and effect of the taint.

2. **Example**:
    - Assume the node has the following taint:
      ```bash
      kubectl taint nodes node1 key=value:NoSchedule
      ```

    - Deploy a Pod with a matching toleration:
     deployment.yaml

   **Explanation**:
    - The taint `key=value:NoSchedule` prevents Pods without a matching toleration from being scheduled on `node1`.
    - The toleration in the Pod allows it to bypass the taint and be scheduled on the node.