# Question 49: Debug a Pod in CrashLoopBackOff

Create a Pod named `broken-shell` with these requirements:

- Use image `busybox:1.36`.
- Start with command `/bin/notfound`.

Then investigate why it fails and fix it so the Pod stays running with command `sh -c "echo ok && sleep 3600"`.
Save the manifest as `pod.yaml`.

