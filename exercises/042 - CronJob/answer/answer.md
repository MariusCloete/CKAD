Apply the CronJob manifest:

```bash
 k create job report-job --image=busybox:1.36 --dry-run=client -o yaml -- sh -c "date; echo report" > cronjob.yaml
```
Then just edit the `cronjob.yaml` file to add the schedule and restartPolicy and cromjob spec:

```yaml
apiVersion: batch/v1
kind: Job
metadata:
  creationTimestamp: null
  name: report-job
spec:
  schedule: "*/5 * * * *"
  jobTemplate:
    spec:
      template:
        metadata:
          creationTimestamp: null
        spec:
          containers:
            - command:
                - sh
                - -c
                - date; echo report
              image: busybox:1.36
              name: report-job
              resources: {}
          restartPolicy: OnFailure

```
      
        



```bash
kubectl apply -f cronjob.yaml
kubectl get cronjob report-job
kubectl describe cronjob report-job
```

This example uses `batch/v1`, which replaces older deprecated CronJob API versions.

