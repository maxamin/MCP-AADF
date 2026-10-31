# Deployment and Configuration

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Operational topology and rollout.

## MVP topology

Single-host MCP gateway, local policy engine, isolated runtime, SQLite evidence index and disposable target fixtures.

## Production-readiness prerequisites

Threat-model review, secrets management, network authentication, backup/restore, signed drivers, access controls, monitoring and incident procedures.

## Configuration

Bind to localhost by default; disable state changes by default; explicit allowlist for targets; log policy decisions.

## Rollout

Start in offline sandbox; add read-only host discovery; then staged platform adapters. No default remote execution.



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
