# Service Entries

## Overview

- `ServiceEntry` registers an external service into the mesh.
- So Istio knows about it, and can communicate with it.

## Setup

### Method 1: Direct from GitHub (no clone needed)
```bash
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/8-service-entries/setup.yaml
```

### Method 2: Local repo path
```bash
kubectl apply -f 2-traffic-management/8-service-entries/setup.yaml
```

## Task

### Task 1 - DNS ServiceEntry
- Create `ServiceEntry` named `cool-se` in the `cool` namesapce.
- Register external host cool-url.lab on port 80 using DNS resolution.

### Task 2 - IP ServiceEntry
- Create `ServiceEntry` named `warm-se` in the `warm` namespace.
- Register external host 'warm-url.lab' which is accessible on `193.184.216.34:80`.
- Note Resolution should be static.

### Task 3 - Virtual Service
- Create a `VirtualService` for host `warm-url.lab` in the `warm` namespace.
- Route HTTP traffic to `warm-url.lab` on port 80

## Validation Checks

```bash
kubectl get serviceentry -n service-entry-lab
```

## Cleanup

```bash
kubectl delete namespace cool --ignore-not-found=true
kubectl delete namespace warm --ignore-not-found=true
```

## Answer

See `2-traffic-management/8-service-entries/answer.yaml`.
