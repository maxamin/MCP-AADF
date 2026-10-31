# Experimental Methodology

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Test research hypotheses without overstating results.

## Research questions

Can drivers discover unfamiliar interfaces? Do generated adapters reduce integration cost? How well do policies block forbidden operations? How accurately can graphs represent trust boundaries?

## Baselines

Compare against manually coded adapters for equivalent CLI, service, web API, GUI and virtual device fixtures.

## Protocol

Fix tool versions, record target images, random seeds, environment settings and expected outputs. Repeat tests and publish failures.

## Metrics

Discovery precision/recall, generation pass rate, hallucinated capability rate, workflow reliability, latency, policy rejection rate, rollback success, maintenance time.



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
