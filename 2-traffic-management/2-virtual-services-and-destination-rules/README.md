# Virtual Services and Destination Rules

## Overview

- `DestinationRule` defines traffic policies and subsets (for example `v1` and `v2`).
- `VirtualService` defines how traffic is routed to those subsets.
- Together, they let you do safe progressive delivery (for example 80/20 rollouts).

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/2-virtual-services-and-destination-rules/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/2-virtual-services-and-destination-rules/setup.yaml
```

## Task

### Task 1 - Basic subset routing
- Create a `DestinationRule` for service `reviews` with subsets `v1` and `v2`.
- Create a `VirtualService` that routes all traffic to subset `v1`.

### Task 2 - Weighted subset routing (20/80)
- Update the `VirtualService` so traffic is split:
  - 20% to subset `v1`
  - 80% to subset `v2`

## Validation Checks

```bash
kubectl get virtualservice,destinationrule -n vs-dr-lab
kubectl get virtualservice reviews -n vs-dr-lab -o yaml
```

## Cleanup

```bash
kubectl delete virtualservice reviews destinationrule reviews -n vs-dr-lab --ignore-not-found=true
kubectl delete namespace vs-dr-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/2-virtual-services-and-destination-rules/answer.yaml`.
