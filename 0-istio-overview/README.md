# Istio Overview

## What is Istio?
Istio is an open-source service mesh for Kubernetes. It manages service-to-service communication, security, and observability without requiring each app team to build that logic into every service.

## What is it used for?
- Traffic management: routing, retries, timeouts, mirroring, load balancing.
- Security: mTLS between services, plus authentication and authorization policies.
- Observability: metrics, logs, and tracing for service-to-service traffic.
- Resilience and policy: consistent behavior across all workloads.

## What is a service mesh?
A service mesh is an infrastructure layer for service-to-service communication.  
It handles networking concerns (security, policy, reliability, visibility) so application code can stay focused on business logic.

## Simple analogy
Imagine every app is a person sending a letter to another person.

If you want to send a letter, you have to go to them and hand it over yourself.
This is like running without a service mesh: each app needs its own built-in way to deliver messages to other apps.

The service mesh acts like a delivery driver that delivers the letters for you.
- It securely delivers each letter.
- It tracks delivery status.
- It follows shared rules for retries and time limits.
- It records what happened so issues can be investigated.

In microservices, your app just writes the message. Istio handles how that message is delivered between services.

## Other service mesh examples
- Linkerd
- Consul service mesh
- Kuma
- Cilium service mesh
- AWS App Mesh
- Traefik Mesh

## Sidecar Mode
- In the sidecar mode, Istio uses an Envoy proxy next to your app container. 
- Every pod will have additonal istio container, this is the envoy proxy.
- The app handles business logic.
- Envoy handles traffic policies, mTLS, telemetry, and retries/timeouts.
- Think of Envoy proxies as the local delivery driver for each app.


> **Terminology note:** The terms **Envoy** and **proxy** is often used interchangeably.


## Istio architecture
### Data plane
- Handles real service-to-service traffic.
- In sidecar mode, this is mostly Envoy proxies.

### Control plane
- Managed by `istiod`.
- Pushes config and certificates to the data plane.
- Acts as certificate authority for mesh identities.

## Ambient mesh (sidecar-less mode)
Ambient mode removes the need for a sidecar on every pod.
Instead of having a proxy per pod, you have a `ztunnel` per node that acts as the delivery driver.
- `ztunnel` runs on each node and handles secure L4 traffic.
- Waypoint proxies are optional L7 proxies for advanced app-layer policy.

