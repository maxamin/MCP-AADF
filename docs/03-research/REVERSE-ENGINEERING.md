# Reverse Engineering Engine

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Authorized static and dynamic software understanding.

## Static

PE/ELF/Mach-O metadata, symbols, imports, dependency graphs, disassembly through approved tools, strings and documented API extraction.

## Dynamic

Debugger attachments to owned test processes, runtime tracing, call relationships, IPC observation, heap and stack layout analysis.

## Integrations

Ghidra, Capstone, GDB, LLDB, Tree-sitter, language servers. Record tool versions and analysis provenance.

## Outputs

Function inventory, interface hypotheses, verified state transitions, binary-to-source mapping where available, uncertainty and limitations.



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
