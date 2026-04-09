# Deployment Label Not Injected

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/4-troubleshooting/2-deployment-label-not-injected/setup.yaml

# Method 2: Local repo path
kubectl apply -f 4-troubleshooting/2-deployment-label-not-injected/setup.yaml
```

## Task

### Task 1 - Find the root cause
- Workload communication is failing even though the namespace appears mesh-enabled.
- Identify the workload-level configuration causing the problem.

### Task 2 - Apply a fix and confirm
- Implement the minimal fix on the workload configuration.
- Restart/reconcile the deployment.
- Confirm new pods include `istio-proxy`.

## Validation Checks

```bash
kubectl get deployment frontend -n deployment-label-lab -o yaml
kubectl get pod -n deployment-label-lab -l app=frontend -o jsonpath='{.items[0].spec.containers[*].name}'
```

## Cleanup

```bash
kubectl delete deployment frontend -n deployment-label-lab --ignore-not-found=true
kubectl delete namespace deployment-label-lab --ignore-not-found=true
```

## Answer

See `4-troubleshooting/2-deployment-label-not-injected/answer.yaml`.
