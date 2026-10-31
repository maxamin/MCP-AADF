# Evidence, Forensics and Provenance

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Reliable and privacy-conscious evidence handling.

## Record

Evidence ID, target, collection method, collector version, timestamp, hashes, sensitivity, retention, chain-of-custody metadata and source references.

## Integrity

Use SHA-256 content hashes and append-only audit events; export manifests with signatures when available.

## Privacy

Prefer metadata to raw memory; redact secrets, restrict access, define retention and deletion policies.

## Findings

Separate observation, inference, validation and recommendation. Never label a theoretical path as confirmed exploitation.



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
