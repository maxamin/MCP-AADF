# Prioritized Engineering Backlog

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Actionable implementation tickets.

## P0

Create Rust workspace; implement gateway health; define JSON schemas; build policy decision API; implement target binding; add audit log; build synthetic CLI fixture; create CI.

## P1

CLI discovery adapter; service inspector; graph persistence; driver registry; sandbox validator; evidence export; adversarial policy tests.

## P2

Ghidra metadata connector; process mapping inspector; virtual serial backend; protocol state machine; differential analyzer; fuzz harness.

## P3

Android emulator integration; cloud inventory; firmware metadata; attestation fixture; self-repair candidates; multi-agent evaluation.

## Ticket template

Objective; threat model impact; acceptance criteria; test fixture; dependencies; documentation; rollback.



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
