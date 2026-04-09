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
- Common pattern: use `RequestAuthentication` to validate tokens, then use `AuthorizationPolicy` to allow specific principals, service accounts, methods, and paths.

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
- Create `AuthorizationPolicy` named `allow-frontend`.
- Scope it to namespace `authz-lab`.
- Allow requests only from principal `cluster.local/ns/authz-lab/sa/frontend`.

### Task 2 - Selector-specific AuthorizationPolicy
- Create `AuthorizationPolicy` named `allow-frontend-httpbin`.
- Add selector `app: httpbin`.
- Allow requests only from principal `cluster.local/ns/authz-lab/sa/frontend`.

### Task 3 - Global AuthorizationPolicy in namespace
- Create `AuthorizationPolicy` named `allow-frontend-global`.
- Do not use a selector.
- Allow requests only from principal `cluster.local/ns/authz-lab/sa/frontend`.

### Task 4 - Basic RequestAuthentication
- Create `RequestAuthentication` named `httpbin-jwt`.
- Attach it to `app: httpbin`.
- Use issuer `testing@secure.istio.io` and the sample jwksUri.

### Task 5 - AuthorizationPolicy allow from service account on a command/path
- Create `AuthorizationPolicy` named `allow-admin-post`.
- Attach it to `app: httpbin`.
- Allow only principal `cluster.local/ns/authz-lab/sa/admin` to `POST` `/post`.

### Task 6 - Deny-all AuthorizationPolicy
- Create `AuthorizationPolicy` named `deny-all-httpbin`.
- Attach it to `app: httpbin`.
- Set action `DENY` with an empty rule.

### Task 7 - Multi-rule AuthorizationPolicy
- Delete `deny-all-httpbin` before you validate this task.
- Create `AuthorizationPolicy` named `api-access`.
- Attach it to `app: httpbin`.
- Add one rule to allow `GET` on `/get`, `/headers`, `/ip`.
- Add one rule to allow principal `cluster.local/ns/authz-lab/sa/admin` to `POST` `/post`.

## Validation Checks

```bash
kubectl get requestauthentication,authorizationpolicy -n authz-lab
kubectl get pods -n authz-lab -o wide
```

## Cleanup

```bash
kubectl delete requestauthentication --all -n authz-lab --ignore-not-found=true
kubectl delete authorizationpolicy --all -n authz-lab --ignore-not-found=true
kubectl delete namespace authz-lab --ignore-not-found=true
```

## Answer

See `3-securing-workloads/2-authorization-policy/answer.yaml`.
