# Architecture Decision Records

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Maintain design decisions as numbered ADRs.

## ADR-0001: Rust execution boundary

Decision: use Rust for policy-sensitive execution and typed driver runtime. Consequence: Python experimentation remains out of the trust boundary.

## ADR-0002: MCP is an interface

Decision: MCP tool calls cannot grant host permissions. Consequence: an independent policy decision point and enforcement point are required.

## ADR-0003: Evidence before capability

Decision: inferred operations are untrusted until validated. Consequence: discovery and activation are separate workflows.

## ADR template

Context; decision; alternatives; consequences; security impact; tests; owner; date; status.



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
