To scale the `api-server` Deployment from 2 replicas to 5 replicas, you can use the following `kubectl` command:

```bash
kubectl scale deployment/api-server --replicas=5
```

### Explanation:
1. **`kubectl scale`**: Scales the specified resource.
2. **`deployment/api-server`**: Specifies the Deployment to scale.
3. **`--replicas=5`**: Sets the desired number of replicas to 5.