# Developer onboarding and contribution workflow

**Status:** design specification; not implemented.

## Prerequisites
Rust stable, Python 3.12+, Git, a supported MCP SDK, SQLite, and an isolated Linux test VM. Pin exact versions in lockfiles at implementation time.

## First contribution
Implement a read-only mock driver: define JSON Schema, create fixture data, implement typed handler, add policy checks, run conformance tests, emit evidence record, and document failure cases.

## Code review checklist
Does this add privileges? Does it broaden target selection? Are inputs bounded? Are error states structured? Is evidence redacted? Is the operation idempotent? Is the test fixture reproducible?

## Documentation convention
Each feature document contains purpose, interfaces, assumptions, threat model, failure modes, acceptance criteria and references. Label aspirational work clearly.

## Release process
Tag versions, publish checksums and SBOM, archive test reports, and document compatibility and breaking changes.
