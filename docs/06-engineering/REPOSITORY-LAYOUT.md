# Repository Layout

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Proposed monorepo tree.

## Tree

```text
mcp-aadf/
├── README.md
├── WHITEPAPER.md
├── ARCHITECTURE.md
├── docs/
├── crates/
│   ├── mcp-gateway/
│   ├── policy-engine/
│   ├── driver-runtime/
│   └── capability-graph/
├── python/
│   ├── discovery/
│   ├── driver_generation/
│   └── research/
├── drivers/
├── fixtures/
├── experiments/
├── schemas/
├── tests/
└── .github/
```

## Separation

Source code, generated drivers, test fixtures and collected evidence MUST be stored separately. Never commit real target dumps or secrets.



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
