# Gateway Label and Virtual Service Port

## Setup

### Method 1: Direct from GitHub (no clone needed)
```bash
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/4-troubleshooting/3-gateway-label-and-virtual-service-port/setup.yaml
```

### Method 2: Local repo path
```bash
kubectl apply -f 4-troubleshooting/3-gateway-label-and-virtual-service-port/setup.yaml
```

## Task

### Task 1 - Find and fix ingress routing issues
- External traffic to `portal.debug.example` that is accessible on port 80 is not reaching the `portal` workload.
- Find and fix the issues.
- Hint there are 3 issues.

## Cleanup

```bash
kubectl delete gateway portal-gateway -n gateway-debug-lab --ignore-not-found=true
kubectl delete virtualservice portal -n gateway-debug-lab --ignore-not-found=true
kubectl delete deployment portal -n gateway-debug-lab --ignore-not-found=true
kubectl delete service portal -n gateway-debug-lab --ignore-not-found=true
kubectl delete namespace gateway-debug-lab --ignore-not-found=true
```

## Answer

See `4-troubleshooting/3-gateway-label-and-virtual-service-port/answer.yaml`.
