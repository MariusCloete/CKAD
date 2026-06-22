To debug the api-pod Pod in the production namespace that is stuck in a CrashLoopBackOff state, use the following commands:
```bash
kubectl describe pod busy-api-pod
kubectl logs busy-api-pod
kubectl event --for pod/busy-api-pod
```
### Explanation:
1. **`kubectl describe pod busy-api-pod`**: This command provides detailed information about the `api-pod`, including its status, events, and any error messages that might indicate why it is in a CrashLoopBackOff state.
2. **`kubectl logs busy-api-pod`**: This command retrieves the logs of the `api-pod`, which can help identify any issues in the application running inside the Pod that might be causing it to crash repeatedly.
3. **`kubectl event --for pod/busy-api-pod`**: This command shows the events related to the `api-pod`, which can provide additional context about why the Pod is failing, such as resource constraints or failed liveness/readiness probes.
4. If the Pod is still in a CrashLoopBackOff state after checking the logs, you may need to investigate further by checking the container image, environment variables, or any dependencies that the application relies on. You can also consider scaling down the Pod and redeploying it if necessary.
5. If you need to get more information about the Pod's resource limits and requests, you can use:

In this case the busy box image need more time to start up. So a delay can be added to the command to give it more time to start up. You can do this by using the `sleep` command in the container's command or entrypoint. For example, you can modify the Pod's spec to include a sleep command before starting the main application.
```bash
kubectl run busy-api-pod --image=busybox --command -- sleep 30 
```