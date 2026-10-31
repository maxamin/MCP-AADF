# Driver lifecycle and ABI

**Status:** design specification; not implemented.

## State machine
`DISCOVERED -> DRAFT -> SCHEMA_VALID -> SANDBOX_TESTED -> APPROVED -> ACTIVE -> DEPRECATED -> REVOKED`. Invalid transitions must fail closed.

## Contract
A driver manifest declares semantic version, supported OS/architecture, target matching rule, operation schemas, side effects, permission requirements, concurrency limits, timeouts, telemetry types and compatibility tests.

## ABI rules
Keep transport independent from adapter logic. Use canonical JSON schemas at the MCP boundary; internally use strongly typed Rust structures. Unknown fields are rejected for state-changing calls. Read-only result envelopes may preserve unknown extension fields.

## Execution envelope
Request ID, correlation ID, target ID, capability ID, argument hash, authorization grant ID, deadline, idempotency key and expected target version. Response contains status, evidence references, structured error, side-effect summary and postcondition status.

## Versioning
Patch releases cannot broaden permissions. Minor releases may add read-only capabilities. Permission-expanding changes require explicit review and a new approval. Persist compatibility matrices per OS and target version.

## Rollback
For state-changing lab fixtures, require a snapshot identifier, cleanup procedure, and verification probe. If rollback cannot be guaranteed, mark operation non-reversible and require additional approval.
