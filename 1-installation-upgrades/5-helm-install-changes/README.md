# Install Ambient Mode with Helm

## Overview

- Ambient mode is Istio's sidecar-less data plane model.
- It uses node-level `ztunnel` and optional waypoint proxies for L7 policies.
- This lab focuses on enabling ambient mode installation.

## Task

### Task 1 - Install ambient profile
- Add the Istio Helm repo.
- Install the ambient-mode components into `istio-system`.

### Task 2 - Verify ambient components
- Confirm `istiod`, `istio-cni`, and `ztunnel` are running in `istio-system`.

## Validation Checks

```bash
helm list -n istio-system
kubectl get daemonset ztunnel -n istio-system
kubectl get pods -n istio-system
```

## Cleanup

```bash
helm uninstall ztunnel -n istio-system
helm uninstall istio-cni -n istio-system
helm uninstall istiod -n istio-system
helm uninstall istio-base -n istio-system
kubectl delete namespace istio-system --ignore-not-found=true
kubectl delete namespace helm-change-lab --ignore-not-found=true
```

## Answer

See `1-installation-upgrades/5-helm-install-changes/answer.yaml`.
