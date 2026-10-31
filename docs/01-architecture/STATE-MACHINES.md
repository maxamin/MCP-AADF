# Lifecycle and State Machines

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Explicit driver and experiment state transitions.

## Driver lifecycle

DISCOVERED → PROPOSED → SCHEMA_VALIDATED → SANDBOX_TESTED → POLICY_APPROVED → ACTIVE → DEPRECATED/REVOKED. Any source change invalidates dependent validation.

## Experiment lifecycle

PLANNED → AUTHORIZED → SNAPSHOTTED → RUNNING → EVALUATING → ROLLBACK → VERIFIED → REPORTED. Failure leads to STOPPED and manual review.

## Invariant

No transition to ACTIVE without successful validation and authorization. No mutable experiment without a rollback strategy.



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
