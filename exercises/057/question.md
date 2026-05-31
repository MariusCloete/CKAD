# Question 57: Create and consume a ConfigMap

Create a `ConfigMap` named `app-config` with these requirements:

- Key `APP_MODE` with value `production`
- Key `app.properties` with content `color=blue`

Then create a Pod named `config-demo` that:

- Uses image `busybox:1.36`
- Consumes `APP_MODE` as an environment variable
- Mounts `app.properties` at `/etc/app/app.properties`
- Runs command `sh -c "printenv APP_MODE; cat /etc/app/app.properties; sleep 3600"`

Save the manifests as `configmap.yaml` and `pod.yaml`, then apply them.

