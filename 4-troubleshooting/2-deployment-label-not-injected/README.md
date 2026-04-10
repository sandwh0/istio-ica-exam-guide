# Deployment Label Not Injected

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/4-troubleshooting/2-deployment-label-not-injected/setup.yaml

# Method 2: Local repo path
kubectl apply -f 4-troubleshooting/2-deployment-label-not-injected/setup.yaml
```

## Task

### Task 1 - Find the root cause of the following issue
- Deployment `frontend`in `lab-two` namespace does nto have a sidecar.
- Identify why and fix.

## Validation Checks

```bash
kubectl get pod -n lab-twp -o yaml
kubectl get pod -n lab-two -l app=frontend -o jsonpath='{.items[0].spec.containers[*].name}'
```

## Cleanup

```bash
kubectl delete deployment frontend -n lab-two --ignore-not-found=true
kubectl delete namespace lab-two --ignore-not-found=true
```

## Answer

See `4-troubleshooting/2-deployment-label-not-injected/answer.yaml`.
