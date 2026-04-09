# Install with IstioOperator

## Overview

- `IstioOperator` lets you define install settings in YAML.
- This is useful when you need repeatable, auditable configuration.
- In this lab you will install Istio with a profile, revision, and egress gateway enabled.

## Task

### Task 1 - Install using IstioOperator
- Create an `IstioOperator` manifest.
- Use profile `demo`.
- Set revision `lab-rev`.
- Enable the egress gateway.
- Install with `istioctl install -f`.

## Validation Checks

```bash
kubectl get deployment -n istio-system
kubectl get deployment istio-egressgateway -n istio-system
kubectl get mutatingwebhookconfiguration | grep lab-rev
```

## Cleanup

```bash
istioctl uninstall --revision lab-rev -y
kubectl delete namespace istio-system --ignore-not-found=true
kubectl delete namespace mesh-customisation --ignore-not-found=true
```

## Answer

See `1-installation-upgrades/3-custom-install-configuration/answer.yaml`.
