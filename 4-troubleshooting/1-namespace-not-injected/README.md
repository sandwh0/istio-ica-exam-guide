# Namespace Not Injected

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/4-troubleshooting/1-namespace-not-injected/setup.yaml

# Method 2: Local repo path
kubectl apply -f 4-troubleshooting/1-namespace-not-injected/setup.yaml
```

## Task

### Task 1 - Find the root cause
- The `frontend` workload in `troubleshoot-ns-injection` is not joining the mesh correctly.
- Identify the configuration issue causing the communication problem.

### Task 2 - Apply a fix and confirm
- Implement the minimal fix.
- Restart/reconcile the workload as needed.
- Confirm the workload now includes `istio-proxy`.

## Validation Checks

```bash
kubectl get ns troubleshoot-ns-injection --show-labels
kubectl get pod -n troubleshoot-ns-injection -l app=frontend -o jsonpath='{.items[0].spec.containers[*].name}'
```

## Cleanup

```bash
kubectl delete deployment frontend -n troubleshoot-ns-injection --ignore-not-found=true
kubectl delete namespace troubleshoot-ns-injection --ignore-not-found=true
```

## Answer

See `4-troubleshooting/1-namespace-not-injected/answer.yaml`.
