# Frequently Asked Questions

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Practical clarification of the concept.

## Is MCP a kernel driver?

No. MCP is an interface and orchestration protocol. Kernel/device capabilities require separate approved backends.

## Can it read every memory region?

No. OS permissions, kernel isolation, hypervisors and hardware TEEs restrict access.

## Can it be used in red-team assessments?

Yes, for authorized post-compromise exposure assessment and controlled adversary emulation, with policy and lab boundaries.

## Is it already implemented?

This package is a proposed architecture and documentation set, not a claim of functioning software.

## What should be built first?

A minimal MCP server, policy engine, two read-only drivers, evidence store and repeatable tests.



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
