Apply the CronJob manifest:

```bash
kubectl apply -f cronjob.yaml
kubectl get cronjob report-job
kubectl describe cronjob report-job
```

This example uses `batch/v1`, which replaces older deprecated CronJob API versions.

