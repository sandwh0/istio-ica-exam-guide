# Retries and Timeouts

## Overview

- `Timeouts` define how long a service waits for a response before returning an error. They stop requests from hanging indefinitely.
- `Retries` define how many times a failed request is attempted again before giving up.
- Both are set in Virtual Services.

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/6-vs-retries-and-timeouts/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/6-vs-retries-and-timeouts/setup.yaml
```

## Task

### Task 1 - Retry policy for HTTP 500
- Create a `VirtualService` for `httpbin` which has a retry with the following settings:
  - 3 attempts
  - Retrying on 5xx errors
  - Try timeout is 2s

### Task 2 - Timeout policy
- Update the same `VirtualService`.
- Add a timeout of 2s

## Validation Checks

```bash
kubectl get virtualservice httpbin -n retries-lab -o yaml
```

## Cleanup

```bash
kubectl delete namespace retries-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/6-vs-retries-and-timeouts/answer.yaml`.
