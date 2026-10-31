# Digital Twins and Autonomous Experiments

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Behavioral simulation and reproducible hypothesis testing.

## Twin model

Describe observable interfaces, state transitions, environment dependencies, timing, and expected error behavior.

## Experiment loop

Observe → propose hypothesis → design bounded test → policy check → snapshot → run → evaluate → record evidence → rollback.

## Limits

Twins are approximations; maintain fidelity scores and known gaps. Never assume a virtual reproduction establishes real-device exploitability.



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
