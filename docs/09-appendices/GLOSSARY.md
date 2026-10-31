# Glossary

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Definitions used throughout the documentation.

## Core terms

**Adaptive driver:** typed integration that exposes verified application capabilities. **MCP:** interoperability protocol for tools/resources/prompts. **Capability graph:** provenance-backed entity/relationship model. **Fixture:** controlled test target. **Policy enforcement point:** runtime guard for actions.

## Security terms

**Privilege boundary:** separation between identities or permission domains. **Persistence surface:** legitimate startup mechanism potentially abused by attackers. **TEE:** hardware-supported isolated execution environment. **Attestation:** evidence about platform or enclave state.

## Evidence terms

**Observed:** directly recorded. **Inferred:** reasoned hypothesis. **Validated:** reproduced under specified conditions. **Unsupported:** no sufficient evidence or backend capability.



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
