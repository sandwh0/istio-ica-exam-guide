# Workload Entries

## Overview

- `WorkloadEntry` models non-Kubernetes workloads (for example VMs) in the mesh.
- `ServiceEntry` can then expose those workloads as routable services.
- `WorkloadGroup` provides reusable bootstrap and identity settings for similar workloads.

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/9-workload-entry/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/9-workload-entry/setup.yaml
```

## Task

### Task 1 - Create workload entry resources
- Create a `WorkloadGroup` named `ledger-vm`.
- Create a `WorkloadEntry` named `ledger-vm-1` with address `192.168.10.10`.
- Ensure labels and service account are consistent.

### Task 2 - Expose workload via ServiceEntry
- Create a `ServiceEntry` named `ledger`.
- Use `MESH_INTERNAL` with `STATIC` resolution.
- Ensure `workloadSelector` matches the `WorkloadEntry` labels.

## Validation Checks

```bash
kubectl get workloadgroup,workloadentry,serviceentry -n workload-entry-lab
```

## Cleanup

```bash
kubectl delete workloadgroup ledger-vm workloadentry ledger-vm-1 serviceentry ledger -n workload-entry-lab --ignore-not-found=true
kubectl delete namespace workload-entry-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/9-workload-entry/answer.yaml`.
