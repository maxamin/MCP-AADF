# Schema Catalog

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Versioned schema registry and compatibility strategy.

## Schemas

driver-manifest.schema.json; capability.schema.json; authorization-request.schema.json; evidence.schema.json; finding.schema.json; experiment.schema.json.

## Versioning

Semantic versioning for driver APIs; schema version included in every artifact; backward compatibility tested.

## Errors

Common codes: INVALID_SCHEMA, TARGET_MISMATCH, POLICY_DENIED, UNSUPPORTED_OPERATION, VALIDATION_FAILED, TIMEOUT, ROLLBACK_FAILED.



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
