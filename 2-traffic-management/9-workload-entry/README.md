# Workload Entries

## Overview

- `WorkloadEntry` lets you register a non-kube workload as part of the mesh.
- Like a VM, bare metal server, amazon ec2 etc.
- You’re basically saying “Hey heres a vm outside of kube, but I want it to be apart of the mesh. Secure the traffic, monitor it etc”

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/9-workload-entry/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/9-workload-entry/setup.yaml
```

## Task

### Task 1 - Create workload entry resources
- Create a `WorkloadEntry` named `the-cabbage-vm` for a VM with the address `192.168.10.10`.
- Ensure it has the label location=external

### Task 2 - Expose workload via ServiceEntry
- Create a ServiceEntry named cabbage in the cabbage namespace.
- Expose the WorkloadEntry using host cabbage.internal.
- Use location: MESH_INTERNAL and resolution: STATIC.
- Ensure the workloadSelector matches the labels on the-cabbage-vm.

## Validation Checks

```bash
kubectl get workloadgroup,workloadentry,serviceentry -n workload-entry-lab
```

## Cleanup

```bash
kubectl delete namespace cabbage --ignore-not-found=true
```

## Answer

See `2-traffic-management/9-workload-entry/answer.yaml`.
