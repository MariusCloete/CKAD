To perform a rolling update for the `web-app` Deployment, upgrading the image from `nginx:1.19` to `nginx:1.21` while ensuring zero downtime, you can use the following `kubectl` command:

Run the following command in your terminal to list containers:
```bash 
kubectl get deployment web-app -o wide
```
```bash
kubectl set image deployment/web-app nginx=nginx:1.21 --record
```
If you have no other container in the deployment, you can omit the container name and use:
```bash
kubectl set image deployment/web-app *=nginx:1.21 --record
```

### Explanation:
1. **`kubectl set image`**: Updates the container image for the specified Deployment.
2. **`deployment/web-app`**: Specifies the Deployment to update.
3. **`nginx=nginx:1.21`**: Updates the container named `nginx` to use the `nginx:1.21` image.
4. **`--record`**: Records the command in the Deployment's revision history for tracking purposes.