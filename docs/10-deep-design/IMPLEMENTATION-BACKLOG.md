# Implementation backlog and dependency graph

**Status:** design specification; not implemented.

## Workstreams
A: Rust core types, error model, broker and capability grants.
B: MCP SDK integration and tool registry.
C: Linux CLI and service read-only adapters.
D: SQLite evidence and graph persistence.
E: Sandboxed generator and driver conformance suite.
F: Reverse-engineering metadata adapter.
G: Device simulator and memory fixture.
H: Security assessment and reporting.

## Dependencies
A precedes B/C/E/H; C precedes meaningful driver generation benchmarks; D precedes graph findings; E precedes self-repair; G requires the policy broker and isolation.

## Definition of done
Code merged, tests passing, docs linked, permissions documented, failure cases covered, reproducible fixture included, benchmark recorded.

## Recommended first vertical slice
`mcp list_tools -> inspect_service -> broker check -> isolated adapter -> evidence record -> graph edge -> report`.

## Deferred
Kernel agents, TEE research, cross-host orchestration and hardware-in-the-loop until policy and sandboxing have been independently reviewed.
