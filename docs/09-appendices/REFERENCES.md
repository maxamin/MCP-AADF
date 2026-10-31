# References and Further Reading

> MCP-AADF documentation | Status: proposed design, not validated implementation.

Starting points; verify version-specific behavior against current official documentation.

## Standards and protocols

- MCP: https://modelcontextprotocol.io/
- NIST SP 800-115: https://csrc.nist.gov/pubs/sp/800/115/final
- OpenTelemetry: https://opentelemetry.io/

## Analysis and security

- MITRE ATT&CK: https://attack.mitre.org/
- MITRE D3FEND: https://d3fend.mitre.org/
- osquery: https://osquery.io/
- Ghidra: https://ghidra-sre.org/
- QEMU: https://www.qemu.org/
- Renode: https://renode.io/

## Engineering

- Rust: https://www.rust-lang.org/
- Playwright: https://playwright.dev/
- Tree-sitter: https://tree-sitter.github.io/tree-sitter/



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
