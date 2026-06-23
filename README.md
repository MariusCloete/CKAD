# CKAD

**Application Design and Build 20%**

- Define, build and modify container images
Choose and use the right workload resource (Deployment, DaemonSet, CronJob, etc.)
Understand multi-container Pod design patterns (e.g. sidecar, init and others)
Utilize persistent and ephemeral volumes

**Application Deployment 20%**

- Use Kubernetes primitives to implement common deployment strategies (e.g. blue/green or canary)
Understand Deployments and how to perform rolling updates
Use the Helm package manager to deploy existing packages
Kustomize

**Application Observability and Maintenance 15%**

- Understand API deprecations
Implement probes and health checks
Use built-in CLI tools to monitor Kubernetes applications
Utilize container logs
Debugging in Kubernetes

**Application Environment, Configuration and Security 25%**

- Discover and use resources that extend Kubernetes (CRD, Operators)
Understand authentication, authorization and admission control
Understand requests, limits, quotas
Understand ConfigMaps
Define resource requirements
Create & consume Secrets
Understand ServiceAccounts
Understand Application Security (SecurityContexts, Capabilities, etc.)

**Services and Networking 20%**

- Demonstrate basic understanding of NetworkPolicies
Provide and troubleshoot access to applications via services
Use Ingress rules to expose applications



** Script to export in the exam **
```bash
export test="kubectl run test --image=nginx:alpine --rm -i --restart=Never"
export out=" --dry-run=client -o yaml "
```

** VI commands **
"Shift v" to select multiple lines in visual mode
" set nu " to show line numbers
"uu" to undo
Select text with "shift+v" and then ">" to indent or "<" to unindent
To find a word use "/" and then type the word and press enter.

** kubectl expain **
The kubectl explain command is your built-in documentation tool for any Kubernetes resource or field. Here are some practical examples:
Basic resource explanation
```bash
kubectl explain pod
kubectl explain deployment
kubectl explain service
kubectl explain <resource> --recursive
```
Drill into specific fields
```bash
kubectl explain pod.spec
kubectl explain pod.spec.containers
kubectl explain pod.spec.containers.resources
kubectl explain deployment.spec.template.spec
```






