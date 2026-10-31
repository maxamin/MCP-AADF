# Data Model and Capability Graph

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Canonical entities, relations, and evidence contracts.

## Entities

Target, Application, Version, Process, Service, Driver, Interface, Operation, Permission, Principal, MemoryMapping, Device, Firmware, Evidence, Finding, Experiment, PolicyDecision.

## Relationships

EXPOSES, DEPENDS_ON, RUNS_AS, MAPS, ACCESSES, MANAGED_BY, OBSERVED_BY, VERIFIED_BY, AUTHORIZED_FOR. Each edge stores source, time, confidence and verification status.

## Data quality

Deduplicate by stable scoped identifiers; distinguish observed vs inferred; expire stale observations; never equate graph reachability with exploitability.

## Storage

SQLite for MVP, content-addressed artifacts on disk, optional graph database later. Migrations MUST be reversible or have documented restore procedures.



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
