# Control-flow reconstruction and validation

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Reconstruct execution paths from imperfect branch evidence and static CFG constraints.

## Pipeline

Decode trace packets; apply mapping and scheduling sideband; align to static blocks; construct ordered block segments; insert explicit gaps; compare with ground-truth coverage.

## Algorithms

CFG-constrained path reconstruction, shortest plausible path only as inference, interval indexing for address mapping, incremental graph updates, and edit-distance alignment between runs.

## Evidence semantics

`observed` blocks are backed by trace data; `inferred` transitions are annotated with constraints; `experimentally_validated` causal claims require repeated interventions.

## Metrics

Block recall/precision against instrumented reference, unresolved address rate, decode failure rate, trace loss, processing throughput, and time-to-graph.

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

