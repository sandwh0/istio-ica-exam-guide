# Change istioctl Installation

## Overview

- After a base install, you often need to change control-plane settings.
- You can apply changes either via command-line `--set` flags or via `IstioOperator` YAML.
- In this lab you will do both for pilot resource requests.

## Task

### Task 1 - Install base Istio with istioctl
- Install Istio with profile `demo`.

### Task 2 - Update pilot resources using command line
- Update pilot requests to CPU `200m` and memory `256Mi`.

### Task 3 - Update pilot resources using IstioOperator
- Apply the same update using an `IstioOperator` file.

## Validation Checks

```bash
kubectl get deployment istiod -n istio-system -o jsonpath='{.spec.template.spec.containers[0].resources.requests}'
```

## Cleanup

```bash
istioctl uninstall --purge -y
kubectl delete namespace istio-system --ignore-not-found=true
kubectl delete namespace operator-change-lab --ignore-not-found=true
```

## Answer

See `1-installation-upgrades/4-istiooperator-changes/answer.yaml`.
