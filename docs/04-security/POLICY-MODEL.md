# Authorization and Policy Model

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Capability-based access controls and independent enforcement.

## Decision inputs

Subject, target, operation, driver digest, environment, approval, expiration, side effects and requested resource limits.

## Rules

Default deny; require exact target identity; reject unknown operation; never allow privilege inheritance through driver composition; re-check at execution time.

## Example

```yaml
policy_version: 1
default: deny
rules:
  - operation: memory.inspect_mappings
    environment: isolated_lab
    target_class: owned_fixture
    decision: allow
  - operation: memory.write_lab_fixture
    environment: isolated_lab
    target_class: owned_fixture
    approval: required
    decision: conditional
```

## Testing

Property-based tests for cross-target denial, expired approval, changed driver digest, unknown capability and model-generated malformed arguments.



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
