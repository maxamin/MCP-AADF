# Implementation Roadmap

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Milestones and evidence-based exit criteria.

## M0: Design

Finalize contracts, threat model, schema, fixture catalog and success metrics.

## M1: Minimal vertical slice

MCP gateway + policy engine + two read-only drivers + evidence store + integration tests.

## M2: Adaptive generation

Propose typed driver from known CLI/API docs; validate in sandbox; quarantine invalid candidates.

## M3: Research intelligence

Binary metadata, memory mappings, graph relationships, privilege-boundary auditing and persistence detection.

## M4: Device and VM lab

Virtual serial/USB fixtures, protocol models, safe connected-device inspection and reproducible simulations.

## M5: Autonomous experimentation

Hypothesis generation, bounded tests, rollback, provenance and benchmark comparison.

## Gate

Each milestone requires documented demos, tests, security review and measured limitations.



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
