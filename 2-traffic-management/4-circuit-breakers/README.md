# Circuit Breakers

## Overview

- Circuit breaking protects services under load or failure conditions.
- In Istio, this is configured in `DestinationRule` traffic policies.
- Typical settings include connection pool limits and outlier detection.

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/4-circuit-breakers/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/4-circuit-breakers/setup.yaml
```

## Task

### Task 1 - Circuit breaker policy
- Create a `DestinationRule` for `httpbin`.
- Set:
  - `http1MaxPendingRequests: 1`
  - `maxRequestsPerConnection: 1`
  - `consecutive5xxErrors: 1`

## Validation Checks

```bash
kubectl get destinationrule httpbin -n circuit-breaker-lab -o yaml
```

## Cleanup

```bash
kubectl delete destinationrule httpbin -n circuit-breaker-lab --ignore-not-found=true
kubectl delete namespace circuit-breaker-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/4-circuit-breakers/answer.yaml`.
