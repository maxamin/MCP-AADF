# Threat Model

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Threats, assets, trust boundaries and mitigations.

## Assets

Authorization records, evidence, driver registry, target systems, host privileges, model context, secrets and research artifacts.

## Adversaries

Malicious driver publisher, compromised target, prompt-injection author, unauthorized local operator, compromised dependency.

## Threats

Tool-output prompt injection, confused deputy, schema smuggling, target substitution, driver supply-chain compromise, unsafe memory access, evidence tampering, resource exhaustion.

## Controls

Fail-closed authorization, sandboxing, signed packages, target binding, read-only defaults, immutable audit references, redaction, deterministic tests and emergency stop.

## Review cadence

Update threat model whenever a new backend, privilege class, network transport or hardware interface is introduced.



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
