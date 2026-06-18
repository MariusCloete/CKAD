# Question 42: Migrate a deprecated CronJob API

Create a `CronJob` named `report-job` with these requirements:

- Use the current supported CronJob API version.
- Schedule: `*/5 * * * *`.
- Use image `busybox:1.36`.
- Run command `sh -c "date; echo report"`.
- Set `restartPolicy` to `OnFailure`.

Save the manifest as `cronjob.yaml` and apply it.

