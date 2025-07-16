A:You need to use kubectl apply with a YAML manifest or use kubectl create with --dry-run and -o yaml to generate the manifest first. For example:
``` bash
kubectl create deployment web-server --image=nginx:latest --dry-run=client -o yaml > web-server.yaml
```
Then, modify the generated YAML to change the kind to DaemonSet and apply it:
``` bash
kubectl apply -f web-server.yaml
```
B:Use kubectl create job with --schedule to create a CronJob, but it requires generating the YAML first since kubectl create does not directly support CronJobs. Here's an example:
``` bash
kubectl create job daily-batch-job --image=busybox:latest --dry-run=client -o yaml > daily-batch-job.yaml
```
```yaml

apiVersion: batch/v1
kind: Job
metadata:
  creationTimestamp: null
  name: daily-batch-job
spec:
  template:
    metadata:
      creationTimestamp: null
    spec:
      containers:
      - image: busybox:latest
        name: daily-batch-job
        resources: {}
      restartPolicy: Never
status: {}

```
Then, modify the generated YAML to change the kind to CronJob and set the schedule:
``` yaml
apiVersion: batch/v1
kind: CronJob
metadata:
  name: daily-batch-job
  namespace: default
spec:
  schedule: "0 0 * * *"
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: batch-job
            image: busybox:latest
            command: ["sh", "-c", "echo 'Running batch job'"]
          restartPolicy: OnFailure
```
Then apply it:
``` bash
kubectl apply -f daily-batch-job.yaml
```
C: You can create the deployment for scenario c using the following single-line command:
``` bash
kubectl create deployment stateless-api --image=node:18-alpine --replicas=3 --dry-run=client -o yaml | kubectl apply -f -
```
