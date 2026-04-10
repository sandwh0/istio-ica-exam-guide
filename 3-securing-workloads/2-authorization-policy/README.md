# Request Authentication and Authorization Policy

## Overview

- `AuthorizationPolicy` controls which services can talk to what inside the mesh.
- Authorization policies have 3 actions:
  - `ALLOW` = allows traffic.
  - `DENY` = blocks traffic.
  - `AUDIT` = logs/audits traffic.
- Important behavior: once you define `ALLOW` policies for a workload, only explicitly allowed traffic is permitted. Everything else is denied.
- `DENY` policies are evaluated before `ALLOW`, so deny rules can block requests even if an allow rule also exists.
- Policies can be namespace-wide (no selector) or workload-specific (with selector).

## Setup

```bash
# Method 1: Direct from GitHub (no clone needed)
kubectl apply -f https://raw.githubusercontent.com/sandwh0/istio-ica-exam-guide/main/3-securing-workloads/2-authorization-policy/setup.yaml

# Method 2: Local repo path
kubectl apply -f 3-securing-workloads/2-authorization-policy/setup.yaml
```

## Task

- Treat each task as a separate exercise unless a task explicitly says to update an existing resource.

### Task 1 - Basic AuthorizationPolicy (allow from frontend service account)
- Create `AuthorizationPolicy` named `allow-frontend` in the `authz-lab` namesapce.
- Allow requests only from the `frontend` service account.

### Task 2 - Selector-specific AuthorizationPolicy
- Create `AuthorizationPolicy` named `allow-frontend-httpbin`.
- Add selector `app: httpbin` in the `authz-lab` namesapce.
- Allow requests only from the `admin` service account to `POST` `/post`.

### Task 3 - Deny-all AuthorizationPolicy
- Create `AuthorizationPolicy` named `deny-all`.
- Set action `DENY` all within the `deny-all` namespace.

### Task 4 - Multi-rule AuthorizationPolicy
- Delete `deny-all-httpbin` before you validate this task.
- Create `AuthorizationPolicy` named `api-access`.
- Attach it to `app: httpbin`.
- Add one rule to allow `GET` on `/get`, `/headers`, `/ip`.
- Add one rule to allow principal `cluster.local/ns/authz-lab/sa/admin` to `POST` `/post`.

## Cleanup

```bash
kubectl delete namespace authz-lab --ignore-not-found=true
kubectl delete namespace adeny-all --ignore-not-found=true
```

## Answer

See `3-securing-workloads/2-authorization-policy/answer.yaml`.
