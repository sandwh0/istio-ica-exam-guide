# Canary Upgrade

## Overview

- Canary upgrades use revision-based control planes.
- You install a newer revision, move namespace labels, and restart workloads.
- This lets you upgrade gradually instead of changing everything at once.

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/1-installation-upgrades/6-canary-upgrade/setup.yaml

# Method 2: Local repo path
kubectl apply -f 1-installation-upgrades/6-canary-upgrade/setup.yaml
```

## Task

### Task 1 - Install lower version revision
- Install an older Istio revision named `1-21-0`.
- Restart `frontend` so it joins revision `1-21-0`.

### Task 2 - Install newer canary revision
- Install a newer Istio revision named `1-22-0`.

### Task 3 - Move workload namespace to new revision
- Switch namespace `canary-upgrade-lab` from `1-21-0` to `1-22-0`.
- Restart `frontend` and verify new pods use the new revision.

## Validation Checks

```bash
kubectl get ns canary-upgrade-lab --show-labels
kubectl get pod -n canary-upgrade-lab -l app=frontend --show-labels
```

## Cleanup

```bash
kubectl delete deployment frontend -n canary-upgrade-lab --ignore-not-found=true
kubectl delete service frontend -n canary-upgrade-lab --ignore-not-found=true
kubectl delete namespace canary-upgrade-lab --ignore-not-found=true
istioctl uninstall --revision 1-22-0 -y
istioctl uninstall --revision 1-21-0 -y
```

## Answer

See `1-installation-upgrades/6-canary-upgrade/answer.yaml`.
