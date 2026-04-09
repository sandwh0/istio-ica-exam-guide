# Install with istioctl

## Overview

- `istioctl` is the simplest way to install Istio for exam-style tasks.
- It supports profiles and inline overrides from the command line.
- In this lab, you will install the `demo` profile and tune pilot resource requests.

## Task

### Task 1 - Fresh install with demo profile
- Install Istio using `istioctl` with the `demo` profile.

### Task 2 - Set pilot resource requests via command line
- Set pilot CPU request to `100m`.
- Set pilot memory request to `128Mi`.

## Validation Checks

```bash
kubectl get deployment istiod -n istio-system
kubectl get deployment istiod -n istio-system -o jsonpath='{.spec.template.spec.containers[0].resources.requests}'
```

## Cleanup

```bash
istioctl uninstall --purge -y
kubectl delete namespace istio-system --ignore-not-found=true
kubectl delete namespace istioctl-lab --ignore-not-found=true
```

## Answer

See `1-installation-upgrades/1-istioctl-install/answer.yaml`.
