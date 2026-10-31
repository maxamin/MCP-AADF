# Open research questions

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Unresolved questions that should guide prototypes instead of being silently assumed solved.

## PT accuracy

How reliably can PT plus sideband reconstruct user-space blocks under context switching, ASLR, and JIT code?

## Marker fidelity

Which data transformations can shadow-memory labels follow without unacceptable overhead?

## Causal attribution

What experimental controls are sufficient to attribute device-triggered execution changes?

## Device fidelity

How do virtual peripheral timings and errors compare with authorized physical traces?

## Cross-host time

How should clock uncertainty propagate through a distributed execution graph?

## Storage

At what event scale does SQLite/Parquet stop being sufficient?

## Automated experiments

How can a planner prove it stays within target scope and resource budgets?

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

