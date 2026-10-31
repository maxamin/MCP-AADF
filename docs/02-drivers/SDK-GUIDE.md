# Driver SDK Guide

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Guidance for third-party driver authors.

## Adapter boundaries

Implement discover(), inspect(), list_capabilities(), execute_authorized(), and healthcheck() using typed inputs and outputs. The runtime injects policy decisions; adapters cannot mint authorization.

## Author checklist

Declare side effects, avoid shell injection, avoid broad filesystem traversal, validate versions, return evidence references, test error handling, redact secrets.

## Packaging

Include manifest, license, compatibility matrix, test fixtures, dependency lockfile, SBOM, and release signature.



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
