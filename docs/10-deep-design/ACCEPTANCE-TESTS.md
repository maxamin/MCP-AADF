# Acceptance tests and quality gates

**Status:** design specification; not implemented.

## Milestone M0
MCP server starts; policy broker rejects an unapproved mutating request; driver registry accepts a validated manifest; evidence records include hashes. No privileged worker yet.

## Milestone M1
Two read-only adapters (CLI and service inspector) pass 100 deterministic fixture tests, including malformed input and missing permissions.

## Milestone M2
Generated adapter passes schema tests, sandbox behavior tests and compatibility matrix. Every generated operation has evidence provenance.

## Milestone M3
Graph queries reconstruct known fixture relationships with measured precision/recall; conflicts are retained and marked.

## Milestone M4
Device emulator reproduces specified state transitions; memory inspector reads only allowlisted fixture regions; rollback is verified for lab writes.

## Release gates
No known critical authorization bypass; reproducible build; SBOM; dependency audit; test artifacts; migration plan; documentation updated; rollback exercised.

## Non-goals
No claim of universal binary understanding, arbitrary enclave access, autonomous privilege escalation, stealth persistence or unbounded post-compromise control.
