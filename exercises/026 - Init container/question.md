# Question 26: Use an init container to prepare shared data

Create a Pod named `init-demo` with these requirements:

- Use an `initContainer` named `write-config` with image `busybox:1.36`.
- The init container writes `color=blue` into `/work/config/app.conf`.
- Main container `app` uses image `busybox:1.36`.
- Main container runs `sh -c "cat /work/config/app.conf && sleep 3600"`.
- Both containers share data using one `emptyDir` volume mounted at `/work/config`.

Save the manifest as `pod.yaml` and apply it.

