# Retries and Timeouts

## Overview

- `VirtualService` can define client behavior with timeout and retry settings.
- Retries help with transient failures.
- Timeouts prevent requests from hanging too long.

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/6-vs-retries-and-timeouts/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/6-vs-retries-and-timeouts/setup.yaml
```

## Task

### Task 1 - Retry policy for HTTP 500
- Create a `VirtualService` for `httpbin`.
- Configure retries:
  - `attempts: 3`
  - `retryOn: 5xx`
  - `perTryTimeout: 2s`

### Task 2 - Timeout policy
- Update the same `VirtualService`.
- Set `timeout: 2s`.

## Validation Checks

```bash
kubectl get virtualservice httpbin -n retries-lab -o yaml
```

## Cleanup

```bash
kubectl delete virtualservice httpbin -n retries-lab --ignore-not-found=true
kubectl delete namespace retries-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/6-vs-retries-and-timeouts/answer.yaml`.
