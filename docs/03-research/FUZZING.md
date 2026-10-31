# Fuzzing and Crash Triage

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Sandboxed test generation and automated triage.

## Scope

Owned test binaries, APIs and simulated peripherals. Use coverage-guided and grammar-aware fuzzing where appropriate.

## Pipeline

Fixture snapshot → generate corpus → execute with resource limits → collect crashes → deduplicate → minimize → classify → report → reset.

## Safety

No fuzzing production targets; cap CPU, memory, disk, network and test duration. No automatic weaponization of crashes.

## Metrics

Coverage, unique crashes, reproducibility, time-to-crash, false-positive rate and regression detection.



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
