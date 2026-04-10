# Virtual Services and Destination Rules

## Overview

- `VirtualService` allow you to configure traffic routing rules. 
  - It controls where traffic is routed inside the mesh.
- `DestinationRule` lets you control how traffic is sent.
  - It would with the virutal Service.
- So while the virtual service is where your traffic goes, desintation rule is how it gets there.

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/2-traffic-management/2-virtual-services-and-destination-rules/setup.yaml

# Method 2: Local repo path
kubectl apply -f 2-traffic-management/2-virtual-services-and-destination-rules/setup.yaml
```

## Task

### Task 1 - Basic subset routing
- Route 80% of the `reviews` traffic to `reviews-v1` and 20% to `reviews-v2`.
- You will need to create a destination rule and a virtual service.


## Cleanup

```bash
kubectl delete namespace weighting-lab --ignore-not-found=true
```

## Answer

See `2-traffic-management/2-virtual-services-and-destination-rules/answer.yaml`.
