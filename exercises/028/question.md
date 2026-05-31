# Question 28: Use a Job for one-time batch work

Create a `Job` named `pi-job` with these requirements:

- Use image `perl:5.34`.
- Run command `perl -Mbignum=bpi -wle 'print bpi(1000)'`.
- Set `completions` to `1`.
- Set `backoffLimit` to `2`.

Save the manifest as `job.yaml` and apply it.

