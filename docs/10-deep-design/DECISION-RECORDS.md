# Architecture decision records

**Status:** design specification; not implemented.

## ADR-001: MCP is the orchestration plane
**Decision:** MCP exposes typed tools, not raw kernel or hardware privileges. **Reason:** protocol interoperability and privilege separation. **Consequence:** specialized backends are required.

## ADR-002: Read-only by default
**Decision:** deny mutations absent scoped grants. **Reason:** reduce unintended side effects. **Consequence:** some workflows need operator approvals.

## ADR-003: Rust broker, Python research tooling
**Decision:** put authorization and worker lifecycle in Rust; allow Python for offline analysis. **Reason:** smaller trusted computing base. **Consequence:** IPC contracts require versioning.

## ADR-004: Evidence first
**Decision:** no capability is promoted without verification evidence. **Reason:** prevent model hallucinations becoming executable authority. **Consequence:** slower initial integration.

## ADR-005: SQLite first
**Decision:** local transactional store before distributed graph infrastructure. **Reason:** reproducibility and simplicity. **Consequence:** scale-out deferred.

## ADR-006: Laboratory writes only
**Decision:** memory/device writes require disposable fixtures and rollback. **Reason:** high consequence and uncertain effects. **Consequence:** production support remains observational.
