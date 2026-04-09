# Gateway Label and Virtual Service Port

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/4-troubleshooting/3-gateway-label-and-virtual-service-port/setup.yaml

# Method 2: Local repo path
kubectl apply -f 4-troubleshooting/3-gateway-label-and-virtual-service-port/setup.yaml
```

## Task

### Task 1 - Find ingress routing issues
- External traffic to `portal.debug.example` is not reaching the `portal` workload.
- Identify the misconfiguration in ingress gateway binding.

### Task 2 - Find service routing issues
- Continue troubleshooting the virtual service route configuration.
- Identify and fix destination targeting problems so traffic reaches the correct service endpoint.

## Validation Checks

```bash
kubectl get gateway,virtualservice -n gateway-debug-lab -o yaml
kubectl get service portal -n gateway-debug-lab
```

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
