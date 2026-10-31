# Cloud, Container and Mobile Extensions

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Future platform adapters and isolation-aware observation.

## Cloud

Read-only inventory of IAM relationships, workloads, Kubernetes RBAC and deployment metadata using scoped provider credentials.

## Containers

Inspect namespaces, cgroups, container metadata, image provenance and runtime policy in controlled clusters.

## Android

Use authorized ADB/debuggable apps, Binder interface metadata, package permissions, emulator fixtures and app lifecycle observations.

## Priority

Not in MVP; establish separate threat models and platform-specific policy controls before enabling.



## Implementation contract

- **Inputs:** Declare typed parameters, target identity, authorization scope and version assumptions.
- **Outputs:** Return structured results, evidence references, confidence and explicit partial-failure states.
- **Isolation:** Use the least-privileged backend, bounded resources and deny-by-default policy.
- **Verification:** Test normal operation, malformed inputs, permission denial, stale target identity, timeouts and cleanup.
- **Acceptance:** Provide reproducible fixtures and measurable success criteria before claiming implementation readiness.

## Open engineering questions

1. Which interfaces can be verified without privileged access?
2. How are version changes detected and cached results invalidated?
3. What telemetry demonstrates correctness and failure?
4. What data must be redacted before reaching a model?
5. What rollback or recovery mechanism applies to state changes?
