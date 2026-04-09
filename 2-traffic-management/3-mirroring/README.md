# Mirroring

## Overview

- Traffic mirroring sends a copy of live traffic to another destination.
- The mirrored request does not affect the live response path.
- This is useful for testing new versions safely with production traffic patterns.

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/3-mirroring/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/3-mirroring/setup.yaml
```

## Task

### Task 1 - Create mirror routing
- Create a `DestinationRule` for `api` with subsets `v1` and `v2`.
- Create a `VirtualService` that routes live traffic to `v1`.
- Mirror 100% of traffic to `v2`.

## Validation Checks

```bash
kubectl get virtualservice,destinationrule -n mirroring-lab
kubectl get virtualservice api -n mirroring-lab -o yaml
```

## Cleanup

```bash
kubectl delete virtualservice api destinationrule api -n mirroring-lab --ignore-not-found=true
kubectl delete namespace mirroring-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/3-mirroring/answer.yaml`.
