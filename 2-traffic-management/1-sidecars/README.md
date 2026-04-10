# Sidecars

## Overview

- A `Sidecar` resource controls the proxy behavior for selected workloads.
- It is used to limit egress hosts and reduce unnecessary config pushed to proxies.
- Think of it as narrowing what a workload is allowed to "see" in the mesh.
- When a namespace is injected, the default sidecar setting is permissive. 

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/1-sidecars/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/1-sidecars/setup.yaml
```

## Task

### Task 1 - Basic Sidecar
- Override the default sidecar in the `sidecar-lab` namespace to allow egress to it self, the istio-system namespace, and the `security` namespace.


### Task 2 - Selector-specific Sidecar
- Create a sidecar named `super-egress` in the `super-security` ns.
- It should only target the payments app.
- Allow egress only to `./*` and `istio-system/*`.

## Cleanup

```bash
kubectl delete namespace sidecar-lab --ignore-not-found=true
kubectl delete namespace security --ignore-not-found=true
kubectl delete namespace super-security --ignore-not-found=true
```

## Answer

See `2-traffic-management/1-sidecars/answer.yaml`.
