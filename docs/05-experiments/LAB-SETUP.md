# Isolated Research Lab

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Reference lab environment and safety controls.

## MVP lab

Linux workstation with rootless containers, disposable VM images, test service, local HTTP API and synthetic memory fixture.

## Extended lab

Windows VM, Android emulator, QEMU/Renode virtual peripherals, simulated network services, and TEE development fixtures when supported.

## Isolation

No production credentials; restricted egress; explicit network topology; snapshot/restore; resource quotas; emergency shutdown.

## Fixture catalog

Each fixture declares owner, image hash, ports, interfaces, expected permissions, safe mutations and reset procedure.



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
