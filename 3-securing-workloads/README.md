# Security

The security section focuses on the policy resources that appear regularly in exam scenarios. The main skill is reading the existing policy posture quickly and then applying the smallest safe change.

## For the exam you should be confident with the following

1. Implement `PeerAuthentication` based on specific requirements.
   - Understand the different mTLS modes.
   - Use selectors to target specific workloads.
   - Implement global `PeerAuthentication` policies where required.
2. Implement `RequestAuthentication` for JWT validation where required.
3. Use `AuthorizationPolicy` to allow or deny traffic.
   - Build policies using selectors, different operators, source namespaces, and/or service accounts.
   - Understand deny and deny-all authorization policy patterns.
