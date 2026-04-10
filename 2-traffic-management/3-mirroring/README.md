# Mirroring

## Overview

- Traffic mirroring sends a copy of live traffic to another destination.
- The mirrored request does not affect the live traffic.
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
- Send traffic from the `api` service to the `api-v1' and mirror 100% of the traffic to `api-v2`

## Cleanup

```bash
kubectl delete namespace mirroring-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/3-mirroring/answer.yaml`.
