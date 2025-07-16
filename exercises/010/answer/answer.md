Key Differences Between Red/Green and Canary Deployments:  
Red/Green Deployment: Involves maintaining two separate environments (Red and Green). The current version runs in the Red environment, while the new version is deployed to the Green environment. Once the new version is verified, traffic is switched to the Green environment.
Canary Deployment: Gradually rolls out the new version to a small subset of users or traffic. If successful, the rollout is expanded until the new version replaces the old one.
**Steps to implement Canary Deployment using kubectl:**
1. **Create a new deployment for the canary version**:
   ```bash
   kubectl create deployment myapp-canary --image=myapp:v2
   ```
2. **Scale the canary deployment to a small number of replicas**:
   ```bash
    kubectl scale deployment myapp-canary --replicas=2
    ```
3. **Update the service to route a percentage of traffic to the canary deployment**:
    ```yaml 
    apiVersion: v1
    kind: Service
    metadata:
      name: myapp-service
    spec:
      selector:
         app: myapp
      ports:
         - protocol: TCP
            port: 80
            targetPort: 8080
      # Route 10% of traffic to the canary deployment
      sessionAffinity: ClientIP
      externalTrafficPolicy: Local
    ```
4. **Monitor the canary deployment**:
5. Use `kubectl get pods` to check the status of the canary deployment and ensure it is running correctly.
6. If the canary deployment is successful, gradually increase the traffic to it by updating the service configuration or scaling up the canary deployment.
7. **Switch traffic to the canary deployment**:
   Once the canary deployment is verified, you can switch all traffic to it by updating the service selector or scaling down the original deployment.
   
   ```bash
   kubectl delete deployment myapp
   kubectl rename deployment myapp-canary myapp
   ```

