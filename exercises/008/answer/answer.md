To debug the api-pod Pod in the production namespace that is stuck in a CrashLoopBackOff state, use the following commands:
```bash
kubectl describe pod api-pod --namespace=production
kubectl logs api-pod --namespace=production
```
### Explanation:
1. **`kubectl describe pod api-pod --namespace=production`**: This command provides detailed information about the `api-pod`, including its status, events, and any error messages that might indicate why it is in a CrashLoopBackOff state.
2. **`kubectl logs api-pod --namespace=production`**: This command retrieves the logs of the `api-pod`, which can help identify any issues in the application running inside the Pod that might be causing it to crash repeatedly.
3. **`--namespace=production`**: Specifies that the Pod is in the `production` namespace. If the Pod is in a different namespace, replace `production` with the appropriate namespace name.
4. If the Pod is still in a CrashLoopBackOff state after checking the logs, you may need to investigate further by checking the container image, environment variables, or any dependencies that the application relies on. You can also consider scaling down the Pod and redeploying it if necessary.
5. If you need to get more information about the Pod's resource limits and requests, you can use:
```bash