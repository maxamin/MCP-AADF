# Inter-Driver Interoperability

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Typed composition without implicit privilege inheritance.

## Contract

Every driver declares input/output schemas, version, side effects, timeouts, privilege requirements, and supported target kinds.

## Composition

Broker negotiates compatible contracts and passes scoped tokens. Driver B does not inherit driver A permissions. Cross-target operations require distinct grants.

## Resilience

Bounded queues, cancellation, idempotency keys for state changes, circuit breakers, trace IDs, and dependency-cycle detection.



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
