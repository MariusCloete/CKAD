1. **What is a NetworkPolicy in Kubernetes, and how does it enhance security?**  
   - A NetworkPolicy is a Kubernetes resource that controls the network traffic to and from Pods. It enhances security by allowing you to define rules for ingress (incoming) and egress (outgoing) traffic, restricting communication between Pods, namespaces, or external IPs.

2. **Explain the difference between ClusterIP, NodePort, and LoadBalancer service types.**  
   - **ClusterIP**: Exposes the Service on an internal IP within the cluster. It is the default type and is only accessible from within the cluster.  
   - **NodePort**: Exposes the Service on a static port on each Node's IP. It allows external access to the Service using `<NodeIP>:<NodePort>`.  
   - **LoadBalancer**: Provisions an external load balancer to expose the Service to the internet. It routes traffic to the NodePort and ClusterIP.

3. **What is an Ingress in Kubernetes, and how does it differ from a Service?**  
   - An Ingress is a Kubernetes resource that manages external HTTP/HTTPS access to Services within the cluster. It provides routing rules, SSL termination, and virtual hosting. Unlike a Service, which exposes Pods, an Ingress acts as a layer to manage traffic routing and load balancing for multiple Services.

4. **Example of creating a NetworkPolicy to restrict traffic to a Pod**:  
   ```yaml
   apiVersion: networking.k8s.io/v1
   kind: NetworkPolicy
   metadata:
     name: restrict-traffic
     namespace: default
   spec:
     podSelector:
       matchLabels:
         app: my-app
     policyTypes:
     - Ingress
     ingress:
     - from:
       - ipBlock:
           cidr: 192.168.1.0/24
       - namespaceSelector:
           matchLabels:
             project: my-namespace
       - podSelector:
           matchLabels:
             role: frontend
       ports:
       - protocol: TCP
         port: 80