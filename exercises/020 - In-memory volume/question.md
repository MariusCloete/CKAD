# Question 20: Use an ephemeral in-memory volume

Create a Pod named `cache-pod` in namespace `default` with these requirements:

- Use image `busybox:1.36`.
- Mount an `emptyDir` volume at `/cache`.
- Configure the `emptyDir` volume to use memory.
- Run a command that writes `ok` to `/cache/health.txt` and then sleeps for 3600 seconds.

Save your manifest as `pod.yaml` and apply it.

