# Rust workspace and crate boundaries

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

An implementable package decomposition with bounded privileges and independent test surfaces.

## Workspace

`aadf-types` (schema), `aadf-policy` (authorization), `aadf-events` (ingestion), `aadf-graph` (queries), `aadf-mcp` (gateway), `aadf-adapter-sdk` (traits), `aadf-experiment` (scheduler), `aadf-storage` (artifacts), `aadf-trace-pt` (optional Linux/Intel), `aadf-emulator` (QEMU/Renode adapter), `aadf-marker` (lab-only), `aadf-cli` (operator).

## Trait contract

`Adapter::probe`, `Adapter::start`, `Adapter::stop`, `Adapter::health`, `Adapter::capabilities`, `Adapter::stream`. Versioned schemas; typed errors; cancellation tokens; resource quotas.

## Security boundaries

The MCP gateway has no direct memory privileges. Elevated collectors are separate least-privilege processes with narrow allowlisted operations.

## Build tiers

Core builds on ordinary x86_64/aarch64 Linux without PT; PT backend is a feature-gated target-specific package. CPU-only CI must still pass.

## Implementation contract

- Every operation carries `experiment_id`, `subject_id`, `authorization_scope`, `adapter_version`, and `evidence_id`.
- The control plane must fail closed for unauthorized or ambiguous operations.
- All event times use a monotonic source plus a separately recorded wall-clock anchor; cross-host ordering requires explicit uncertainty.
- Tests must cover successful capture, empty observations, partial data, permission denial, cancellation, crash recovery, and replay.
- All inferred claims must reference raw observations; a graph edge is not proof of causation unless validated by controlled intervention.

## Acceptance criteria

1. An isolated test fixture produces a documented, deterministic expected output.
2. The adapter publishes its capabilities and limitations, including unsupported host features.
3. Raw evidence, transformation version, and normalized output can be independently audited.
4. A CI test demonstrates no silent data loss or unauthorized state modification.

