# 🛠️ Debugging a Failing Pod

Setup
```bash
kubectl run busy-api-pod --image=busybox
```

A Pod named `busy-api-pod` in the `defualt` namespace is stuck in a `CrashLoopBackOff` state. Investigate the issue by checking the logs and describing the Pod.

Provide the `kubectl` commands required to debug this Pod.