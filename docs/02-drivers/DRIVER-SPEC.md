# Adaptive Driver Specification

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Normative driver contract for generated and handwritten adapters.

## Required fields

driver_id, version, supported_platforms, target_matcher, operations, input_schema, output_schema, permissions, side_effects, evidence_requirements, timeouts, compatibility.

## Operation classes

OBSERVE (read-only), ANALYZE (offline), SIMULATE (isolated lab), MUTATE_LAB (reversible test fixture), ADMIN_CHANGE (separate approval; not in MVP).

## Validation

Parse schema, check operation class, verify target binding, run fixture tests, check side effects, fuzz malformed inputs, reject unknown operations.

## Example

```json
{
  "driver_id": "demo.service.inspect",
  "version": "0.1.0",
  "platforms": ["linux"],
  "operations": [{"name": "inspect", "class": "OBSERVE", "permission": "service.read", "approval_required": false}],
  "evidence_required": true
}
```



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
