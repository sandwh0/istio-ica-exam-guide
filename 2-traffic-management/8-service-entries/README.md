# Service Entries

## Overview

- `ServiceEntry` adds external services into Istio's service registry.
- This lets mesh traffic policies apply to services outside the cluster.
- Common patterns are DNS-based external services and static IP-based services.

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/8-service-entries/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/8-service-entries/setup.yaml
```

## Task

### Task 1 - DNS ServiceEntry
- Create `ServiceEntry` named `httpbin-external`.
- Allow HTTPS access to `httpbin.org` on port `443`.
- Use `location: MESH_EXTERNAL` and `resolution: DNS`.

### Task 2 - IP ServiceEntry
- Create `ServiceEntry` named `example-ip-external`.
- Model external host `example-ip.external` with address `93.184.216.34`.
- Use `location: MESH_EXTERNAL` and `resolution: STATIC`.

## Validation Checks

```bash
kubectl get serviceentry -n service-entry-lab
```

## Cleanup

```bash
kubectl delete serviceentry httpbin-external example-ip-external -n service-entry-lab --ignore-not-found=true
kubectl delete namespace service-entry-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/8-service-entries/answer.yaml`.
