# Gateways

## Overview

- `Gateway` controls how traffic enters the mesh at the edge.
- Thing of this the front door of your mesh.
- When tied with a `VirtualService` it controls how that ingress traffic is routed to services.

## Setup

### Method 1: Direct from GitHub (no clone needed)
```bash
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/7-gateways/setup.yaml
```

### Method 2: Local repo path
```bash
kubectl apply -f 2-traffic-management/7-gateways/setup.yaml
```

## Task

### Task 1 - HTTP gateway and virtual service
- An external host `example.lab` must be exposed on port 80.
- Create a `Gateway` for host `example.lab`.
- Create a `VirtualService` bound to that gateway and route traffic to service `example-server` on port 8080.

### Task 2 - TLS gateway and virtual service
- Add an HTTPS server to the same Gateway.
- Configure it to listen on port 443.
- Use SIMPLE TLS mode with credential `portal-tls`.


## Cleanup

```bash
kubectl delete namespace gateway-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/7-gateways/answer.yaml`.
