# Install with Helm

## Overview

- Helm is another supported Istio install path.
- You install `base` first, then `istiod`.
- This is common in environments that standardize on Helm release workflows.

## Task

### Task 1 - Install Istio using Helm
- Add the Istio Helm repo.
- Install `istio-base` and `istiod` into `istio-system`.

## Validation Checks

```bash
helm list -n istio-system
kubectl get deployment istiod -n istio-system
```

## Cleanup

```bash
helm uninstall istiod -n istio-system
helm uninstall istio-base -n istio-system
kubectl delete namespace istio-system --ignore-not-found=true
kubectl delete namespace helm-install-lab --ignore-not-found=true
```

## Answer

See `1-installation-upgrades/2-helm-install/answer.yaml`.
