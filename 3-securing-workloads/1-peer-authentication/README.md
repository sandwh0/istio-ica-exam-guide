# Peer Authentication

## Overview

- `PeerAuthentication` controls how services authenticate with each other inside the mesh using mTLS.
- It answers: when traffic arrives at my service, do I require mTLS encryption, or will I accept plain text too?
- You can apply it at mesh level, namespace level, or workload level (using selectors).
- Most restrictive scope wins, so selector-based policies can override namespace defaults.
- There are 3 modes:
  - `STRICT` = only mTLS allowed.
  - `PERMISSIVE` = both mTLS and plain text allowed.
  - `DISABLE` = only plain text allowed (mTLS rejected).

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/3-securing-workloads/1-peer-authentication/setup.yaml

# Method 2: Local repo path
kubectl apply -f 3-securing-workloads/1-peer-authentication/setup.yaml
```

## Task

### Task 1 - Basic PeerAuthentication (namespace level)
- Create a `PeerAuthentication` called `default` in `peer-auth-lab`.
- Enforce strict mTLS.

### Task 2 - Selector-specific PeerAuthentication
- Create a `PeerAuthentication` called `backend-strict` in `peer-auth-lab`.
- Apply it only to workloads with label `app: backend`.
- Enforce strict mTLS.

### Task 3 - Global PeerAuthentication (mesh wide)
- Create a `PeerAuthentication` called `global-strict` in `istio-system`.
- Enforce strict mTLS mesh-wide.

## Validation Checks

```bash
kubectl get peerauthentication -n peer-auth-lab
kubectl get peerauthentication global-strict -n istio-system -o yaml
```

## Cleanup

```bash
kubectl delete peerauthentication default backend-strict -n peer-auth-lab --ignore-not-found=true
kubectl delete peerauthentication global-strict -n istio-system --ignore-not-found=true
kubectl delete namespace peer-auth-lab --ignore-not-found=true
```

## Answer

See `3-securing-workloads/1-peer-authentication/answer.yaml`.
