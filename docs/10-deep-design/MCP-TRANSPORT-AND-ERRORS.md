# MCP transport and errors

**Status:** design specification; not implemented.

## MCP boundary
Use the official SDK's negotiated protocol version and supported transport. Do not invent protocol-level methods; names like `driver.inspect` are application tool identifiers.

## Tool schemas
Each tool declares input JSON Schema, read-only or mutating classification, target selector, maximum payload size and response envelope. Never expose generic unrestricted shell execution as an MCP tool.

## Errors
Standardize application errors: `INVALID_ARGUMENT`, `TARGET_CHANGED`, `NOT_AUTHORIZED`, `CAPABILITY_UNAVAILABLE`, `TIMEOUT`, `WORKER_FAILED`, `POSTCONDITION_FAILED`, `PARTIAL_RESULT`, `EVIDENCE_UNAVAILABLE`.

## Timeouts and cancellation
Use deadlines propagated to workers. Cancellation stops new actions but cannot guarantee rollback of already committed effects. Report partial completion accurately.

## Streaming
Emit progress events with monotonically increasing sequence numbers; preserve final evidence references. Avoid streaming sensitive memory bytes to general agent context.

## Compatibility
Maintain conformance tests against pinned SDK versions and document any negotiated feature assumptions.
