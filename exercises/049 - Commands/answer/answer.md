Example debugging flow:

```bash
kubectl apply -f pod.yaml
kubectl get pod broken-shell
kubectl describe pod broken-shell
kubectl logs broken-shell
```

The failure comes from the invalid command `/bin/notfound`.

Use the fixed manifest in `pod.yaml`, which contains:

```yaml
command:
  - sh
  - -c
  - echo ok && sleep 3600
```

Then recreate the Pod:

```bash
kubectl delete pod broken-shell
kubectl apply -f pod.yaml
kubectl get pod broken-shell
```

