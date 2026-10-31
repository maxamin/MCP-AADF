# Validation Test Matrix

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Minimum integration and security tests.

## Functional

CLI discovery; HTTP API schema validation; service inspection; virtual serial enumeration; cross-driver telemetry; evidence graph insertion.

## Adversarial

Malicious tool descriptions; schema injection; unauthorized target; expired token; excessive memory range; driver digest change; forged output.

## Safety

Abort on unexpected side effect; reject real device without authorization; deny enclave content read; fail closed when policy unavailable.

## Exit criteria

No bypass of deny cases, all state-changing fixtures reset, reproducible results and explicit unresolved limitations.



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
