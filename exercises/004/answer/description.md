```bash 
kubectl create configmap app-config --from-literal=APP_ENV=production --from-literal=APP_DEBUG=false
```
*add commands "env && sleep 3600"*
- **env**: Print all environment variables in the container, allowing you to verify that the APP_ENV and APP_DEBUG variables have been correctly set from the ConfigMap.
- **sleep 3600**: Keep the container running for 3600 seconds (1 hour) so you can inspect it or troubleshoot if needed. Without this, the container would exit immediately after printing the environment variables.

```bash
kubectl run app-pod --image=busybox --command -- sh -c "env && sleep 3600" --env=APP_ENV=production --env=APP_DEBUG=false
```