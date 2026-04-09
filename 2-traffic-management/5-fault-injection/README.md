# Fault Injection

## Overview

- Fault injection lets you simulate failures intentionally.
- This is used to test retries, timeouts, and client behavior under bad conditions.
- Common fault types are delay and abort (error response).

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/5-fault-injection/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/5-fault-injection/setup.yaml
```

## Task

### Task 1 - Delay fault
- Create a `VirtualService` for `ratings`.
- Inject a fixed delay of `5s` on 100% of requests.

### Task 2 - Error fault
- Update the same `VirtualService`.
- Inject an HTTP abort fault with status code `503` on 100% of requests.

## Validation Checks

```bash
kubectl get virtualservice ratings -n fault-injection-lab -o yaml
```

## Cleanup

```bash
kubectl delete virtualservice ratings -n fault-injection-lab --ignore-not-found=true
kubectl delete namespace fault-injection-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/5-fault-injection/answer.yaml`.
