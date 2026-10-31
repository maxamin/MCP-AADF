# Driver Generation and Validation

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Evidence-first driver synthesis.

## Pipeline

Gather documentation and metadata → infer candidate operations → construct schema → compile/typecheck → static security checks → run fixture tests → compare observations → approve activation.

## Acceptance

Candidate must demonstrate at least one successful positive test, one rejected invalid input, correct side-effect classification, and provenance linking the operation to source evidence.

## Self-repair

When application fingerprint changes, quarantine affected operations, generate a patch candidate, re-run full validation, and require approval before activation.



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
