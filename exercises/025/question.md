# Question 25: Use a CronJob for scheduled work

Create a nightly cleanup task with these requirements:

- Use a `CronJob` named `nightly-cleanup`.
- Schedule: `0 2 * * *`.
- Use image `busybox:1.36`.
- Run command `sh -c "echo cleanup && date"`.

Save the manifest as `cronjob.yaml` and apply it.

