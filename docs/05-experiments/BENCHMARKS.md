# Benchmarks and Evaluation

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Quantitative evaluation definitions.

## Discovery precision

Verified discovered capabilities / all claimed discovered capabilities.

## Discovery recall

Verified discovered capabilities / all capabilities in the curated reference inventory.

## Generation pass rate

Validated generated drivers / all generated candidates.

## Policy rejection

Denied unauthorized test invocations / total unauthorized test invocations. Target 100% in designed test cases; report confidence intervals where meaningful.

## Reliability

Successful authorized workflows / attempted authorized workflows; stratify by target, version and operation class.

## Reproducibility

Store manifest, seed, image digest, tool versions, expected result, observed result and artifact hashes.



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
