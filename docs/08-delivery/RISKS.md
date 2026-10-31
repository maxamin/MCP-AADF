# Risk Register

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Engineering and research risks.

## R1: Overbreadth

Too many platforms before a working vertical slice. Mitigation: stage gates and strict MVP.

## R2: Model hallucination

Unsupported commands or schemas. Mitigation: evidence verification and sandbox tests.

## R3: Privilege concentration

Gateway becomes a high-value target. Mitigation: separation, sandboxing and minimal permissions.

## R4: Hardware variance

Device tests are not reproducible. Mitigation: simulated fixtures and hardware manifests.

## R5: False vulnerability claims

Graph relation mistaken for exploitability. Mitigation: confidence taxonomy and manual review.



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
