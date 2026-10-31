# MCP API Surface

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Illustrative MCP-facing tools and resource semantics.

## Tools

application.discover, application.inspect, driver.propose, driver.validate, driver.activate, graph.query, security.audit, memory.inspect_mappings, device.inspect, experiment.plan, experiment.run_approved, evidence.export.

## Resources

Read-only versioned resources for driver schemas, target metadata, experiment manifests, validation results, and evidence summaries.

## Protocol semantics

Validate arguments before dispatch; return structured errors with machine-readable codes; redact sensitive outputs; enforce quotas. Tool names are application-defined, not MCP standard methods.

## Compatibility

Pin MCP SDK and protocol versions; contract-test tool discovery, invocation, cancellation and error handling across supported clients.



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
