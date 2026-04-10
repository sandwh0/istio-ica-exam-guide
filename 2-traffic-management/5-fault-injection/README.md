# Fault Injection

## Overview

- Fault injection lets deliberately add error and/or delays to your service.
- This is good for testing, to seee how your service / environment handles these.


## Setup

### Method 1: Direct from GitHub (no clone needed)
```bash
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/5-fault-injection/setup.yaml
```

### Method 2: Local repo path
```bash
kubectl apply -f 2-traffic-management/5-fault-injection/setup.yaml
```

## Task

### Task 1 - Delay fault
- Create a `VirtualService` in `ratings` namespace the for `ratings` service.
- Inject a fixed delay of `5s` on 100% of requests.

### Task 2 - Error fault
- Create a `VirtualService` in `api` namespace the for `api-server` service.
- Have it abort 100% of the traffic with a `501` error code where the header is end-user=test-account
- The rest of the traffic should continue to `api-server` as normal

## Validation Checks

```bash
kubectl get virtualservice ratings -n fault-injection-lab -o yaml
```

## Cleanup

```bash
kubectl delete namespace ratings --ignore-not-found=true
kubectl delete namespace api --ignore-not-found=true
```

## Answer

See `2-traffic-management/5-fault-injection/answer.yaml`.
