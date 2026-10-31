# Phased implementation plan

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

A deliverable-based sequence that prevents the research program from collapsing under its own scope.

## Phase 0 — repo hygiene

Schemas, CI, threat model, signed experiment manifests, fixture binaries, documentation link checker. Exit: reproducible build on low-memory host.

## Phase 1 — observation core

Rust events, storage, capability probe, read-only MCP tools, compiler coverage adapter. Exit: event-to-graph deterministic demo.

## Phase 2 — PT and static bridge

Intel PT optional adapter, sideband, Ghidra export, symbolization. Exit: PT versus reference coverage report on supported hardware.

## Phase 3 — marker and device labs

DynamoRIO marker tracer, QEMU device activity scenarios, provenance. Exit: synthetic marker and device replay tests.

## Phase 4 — causal experiments

Differential run planner, repeatability checks, causal evidence grades, trace-gap diagnostics. Exit: documented controlled intervention result.

## Phase 5 — frontier research

Protocol inference, bounded symbolic exploration, PANDA/Renode integration, fuzzing, advanced graph analysis. Exit: peer-reviewable benchmarks.

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

