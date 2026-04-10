# Circuit Breakers

## Overview

- Circuit breaking protects services under load or failure conditions.
- It can stop sending traffic to a service that is failing or overwhelmed.
- This is configured in `DestinationRule` traffic policies.

## Setup

### Method 1: Direct from GitHub (no clone needed)
```bash
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/4-circuit-breakers/setup.yaml
```

### Method 2: Local repo path
```bash
kubectl apply -f 2-traffic-management/4-circuit-breakers/setup.yaml
```

## Task

### Task 1 - Circuit breaker policy
- Create a `DestinationRule` for `httpbin` service.
- Apply it in the `circuit-breaker-lab` namespace.
- Set:
  - 1 max connection
  - 5 max requests per connection
  - 2 consetive 5xx errors 

## Validation Checks

```bash
kubectl get destinationrule httpbin -n circuit-breaker-lab -o yaml
```

## Cleanup

```bash
kubectl delete namespace circuit-breaker-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/4-circuit-breakers/answer.yaml`.
