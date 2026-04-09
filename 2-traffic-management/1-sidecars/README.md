# Sidecars

## Overview

- A `Sidecar` resource controls the proxy behavior for selected workloads.
- It is commonly used to limit egress hosts and reduce unnecessary config pushed to proxies.
- Think of it as narrowing what a workload is allowed to "see" in the mesh.

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/1-sidecars/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/1-sidecars/setup.yaml
```

## Task

### Task 1 - Basic Sidecar
- Create a namespace-level `Sidecar` named `default-egress`.
- Allow egress only to `./*` and `istio-system/*`.

### Task 2 - Selector-specific Sidecar
- Create a workload-specific `Sidecar` named `frontend-egress`.
- Match only `app: frontend`.
- Allow egress only to `./*` and `istio-system/*`.

## Validation Checks

```bash
kubectl get sidecar -n sidecar-lab
kubectl get sidecar default-egress frontend-egress -n sidecar-lab -o yaml
```

## Cleanup

```bash
kubectl delete sidecar default-egress frontend-egress -n sidecar-lab --ignore-not-found=true
kubectl delete namespace sidecar-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/1-sidecars/answer.yaml`.
