# Troubleshooting

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Common failure modes and diagnostic workflow.

## Discovery empty

Check permissions, target scope, platform backend and metadata source availability.

## Driver rejected

Inspect schema errors, missing evidence, unsupported version, changed digest or policy denial.

## Experiment inconsistent

Check clock, random seed, fixture image, concurrent processes, resource limits and cleanup state.

## Graph duplicates

Check scoped identity keys, import provenance and stale observation reconciliation.



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
