# Namespace and Manual Injection

## Overview

- Namespace injection automatically adds sidecars to new pods.
- Manual injection uses `istioctl kube-inject` to generate injected manifests.
- Both approaches are common exam tasks.

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/1-installation-upgrades/7-istio-injection/setup.yaml

# Method 2: Local repo path
kubectl apply -f 1-installation-upgrades/7-istio-injection/setup.yaml
```

## Task

### Task 1 - Namespace injection
- Enable auto-injection for `injection-auto`.
- Restart deployment `frontend` and confirm `istio-proxy` exists.

### Task 2 - Manual injection in non-injected namespace
- Create namespace `injection-manual` without injection label.
- Manually inject and apply the deployment manifest from `manual-demo` ConfigMap.
- Confirm `istio-proxy` exists in manual namespace.

## Validation Checks

```bash
kubectl get pod -n injection-auto -l app=frontend -o jsonpath='{.items[0].spec.containers[*].name}'
kubectl get pod -n injection-manual -l app=frontend -o jsonpath='{.items[0].spec.containers[*].name}'
```

## Cleanup

```bash
kubectl delete deployment frontend -n injection-auto --ignore-not-found=true
kubectl delete service frontend -n injection-auto --ignore-not-found=true
kubectl delete configmap manual-demo -n injection-auto --ignore-not-found=true
kubectl delete deployment frontend -n injection-manual --ignore-not-found=true
kubectl delete namespace injection-auto --ignore-not-found=true
kubectl delete namespace injection-manual --ignore-not-found=true
```

## Answer

See `1-installation-upgrades/7-istio-injection/answer.yaml`.
