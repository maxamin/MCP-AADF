# Protocol and State-Machine Inference

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Derive validated interface models from observed authorized interactions.

## Approach

Capture permitted requests and responses, cluster message types, infer candidate transitions, generate harmless probes, and compare predicted with observed results.

## Models

Finite-state machines, request/response schemas, timing constraints, error states and version-specific behavior.

## Limitations

Encrypted protocols, hidden states and nondeterministic behavior limit inference; do not treat guesses as verified facts.



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
