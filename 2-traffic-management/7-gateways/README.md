# Gateways

## Overview

- `Gateway` controls how traffic enters the mesh at the edge.
- `VirtualService` controls how that ingress traffic is routed to services.
- You will usually configure these together for HTTP/HTTPS ingress.

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/7-gateways/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/7-gateways/setup.yaml
```

## Task

### Task 1 - HTTP gateway and virtual service
- Create a `Gateway` listening on port `80` for host `portal.gateway-lab.example`.
- Create a `VirtualService` bound to that gateway.
- Route traffic to service `portal` port `8080`.

### Task 2 - TLS gateway and virtual service
- Use secret `portal-tls` from `gateway-lab`.
- Add HTTPS server on port `443` using `SIMPLE` TLS mode.
- Ensure `VirtualService` includes host `portal-tls.gateway-lab.example` and routes to `portal:8080`.

## Validation Checks

```bash
kubectl get gateway,virtualservice -n gateway-lab
kubectl get secret portal-tls -n gateway-lab
```

## Cleanup

```bash
kubectl delete gateway portal-gateway virtualservice portal -n gateway-lab --ignore-not-found=true
kubectl delete secret portal-tls -n gateway-lab --ignore-not-found=true
kubectl delete namespace gateway-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/7-gateways/answer.yaml`.
