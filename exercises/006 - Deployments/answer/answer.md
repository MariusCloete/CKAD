To scale the `api-server` Deployment from 1 replicas to 2 replicas, you can use the following `kubectl` command:

```bash
kubectl scale deployment/api-server --replicas=2
```

### Explanation:
1. **`kubectl scale`**: Scales the specified resource.
2. **`deployment/api-server`**: Specifies the Deployment to scale.
3. **`--replicas=2`**: Sets the desired number of replicas to 2.