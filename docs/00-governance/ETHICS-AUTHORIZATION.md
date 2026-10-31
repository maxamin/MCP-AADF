# Authorization and Research Boundaries

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Research is restricted to owned, expressly authorized, or isolated synthetic targets.

## Authorization record

Record operator, target identifier, owner approval, allowed capabilities, start/end window, lab/production classification, and revocation path.

## Prohibited autonomous actions

No stealth persistence, unauthorized credential access, privilege-escalation exploitation, arbitrary memory patching, or unauthorized lateral movement.

## Sensitive data

Minimize collection; redact secrets and personal data; encrypt evidence at rest; set retention and deletion controls.

## Stop conditions

Stop on unexpected privilege, target mismatch, unrecognized physical device, rollback failure, or unsafe actuator state.



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
