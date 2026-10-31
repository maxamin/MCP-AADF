# Post-Compromise Assessment

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Authorized post-compromise exposure and trust-boundary analysis.

## Purpose

From a defined authorized execution context, inventory accessible services, configuration exposures, permissions and security telemetry.

## Modules

Privilege-boundary assessment, startup/persistence artifact detection, process exposure review, detection validation and evidence-backed reporting.

## Boundaries

No autonomous credential harvesting, exploitation, stealth persistence, unauthorized movement or security-control bypass. Use benign reversible lab artifacts for detection testing.

## Reporting

For each finding: evidence, preconditions, confidence, impact hypothesis, reproduction in lab, mitigations and uncertainty.



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
