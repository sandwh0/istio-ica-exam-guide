# Install Ambient Mode with istioctl

## Overview

- Ambient mode is Istio's sidecar-less data plane model.
- It uses node-level `ztunnel` and optional waypoint proxies for L7 policies.
- This lab focuses on installing the ambient profile with `istioctl`.

## Task

### Task 1 - Install ambient profile
- Install Istio with `istioctl` using the `ambient` profile.

### Task 2 - Verify ambient components
- Confirm `istiod`, `istio-cni`, and `ztunnel` are running in `istio-system`.

## Validation Checks

```bash
kubectl get deployment istiod -n istio-system
kubectl get daemonset istio-cni-node -n istio-system
kubectl get daemonset ztunnel -n istio-system
kubectl get pods -n istio-system
```

## Cleanup

```bash
istioctl uninstall --purge -y
kubectl delete namespace istio-system --ignore-not-found=true
```

## Answer

See `1-installation-upgrades/4-install-ambient-mode/answer.yaml`.
