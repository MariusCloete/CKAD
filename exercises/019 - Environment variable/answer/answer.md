You can patch a Kubernetes Deployment to add a new environment variable to all containers using the kubectl patch command with a JSON patch. Here's an example
of how to do this:

```bash
kubectl patch deployment <deployment-name> -p '{"spec": {"template": {"spec": {"containers": [{"name": "<container-name>", "env": [{"name": "<ENV_VAR_NAME>", "value": "<ENV_VAR_VALUE>"}]}]}}}}'
```
or even better

```bash
kubectl set env deployment/<deployment-name> <ENV_VAR_NAME>=<value>
```
in the second command, you can also specify the container name if you have multiple containers in the deployment:

```bash
kubectl set env deployment/<deployment-name> <ENV_VAR_NAME>=<value> --container=<container-name>
``` 
and to remove a environment variable:

```bash
kubectl set env deployment/<deployment-name> <ENV_VAR_NAME>- --container=<container-name>
```


