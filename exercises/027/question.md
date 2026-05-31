# Question 27: Use a sidecar container for log streaming

Create a Pod named `sidecar-log-pod` with these requirements:

- Main container `app` uses `busybox:1.36` and writes a timestamp to `/var/log/app.log` every 5 seconds.
- Sidecar container `log-reader` uses `busybox:1.36` and runs `tail -f /var/log/app.log`.
- Use one shared `emptyDir` volume mounted at `/var/log` in both containers.

Save the manifest as `pod.yaml` and apply it.

