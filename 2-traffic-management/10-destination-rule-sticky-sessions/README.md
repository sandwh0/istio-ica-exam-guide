# Virtual Services (Redirect and Header Match)

## Overview

- `VirtualService` controls request matching and routing behavior.
- You can match on URI, headers, methods, and more.
- Common actions include redirects and route rules based on request attributes.

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/10-destination-rule-sticky-sessions/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/10-destination-rule-sticky-sessions/setup.yaml
```

## Task

### Task 1 - URI prefix redirect
- Create a `VirtualService` named `web`.
- Match URI prefix `/old`.
- Redirect requests to `/new`.

### Task 2 - Exact header match route
- Add another HTTP rule in the same `VirtualService`.
- Match header `x-lab-user` exactly equal to `canary`.
- Route matching requests to service `web` on port `80`.

## Validation Checks

```bash
kubectl get virtualservice web -n virtualservice-lab -o yaml
```

## Cleanup

```bash
kubectl delete virtualservice web -n virtualservice-lab --ignore-not-found=true
kubectl delete namespace virtualservice-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/10-destination-rule-sticky-sessions/answer.yaml`.
