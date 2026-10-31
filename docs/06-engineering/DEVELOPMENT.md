# Development Guide

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Contributor setup and implementation conventions.

## Toolchain

Rust stable toolchain, Python 3.12+, Git, container runtime, pytest and cargo test. Pin actual versions in lockfiles once implementation begins.

## Workflow

Create issue → design contract → write fixture → implement adapter → unit tests → integration tests → policy tests → documentation → review.

## Conventions

Typed schemas, no shell-string interpolation, structured errors, tracing IDs, deterministic fixtures, strict linting and formatting.

## Definition of done

Tests pass, threat model updated, documentation changed, compatibility recorded, evidence examples included, no unresolved critical security issues.



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
