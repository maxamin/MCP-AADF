# Graph storage and query planner

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

An evidence-first execution and capability graph suitable for millions of events.

## Data model

Nodes: experiment, subject, process, thread, binary, module, basic block, memory object, device, driver, observation, hypothesis, artifact. Edges: `observed_at`, `reads`, `writes`, `happens_before`, `mapped_to`, `inferred_from`, `tested_by`.

## Storage

Keep immutable raw chunks in content-addressed storage; maintain normalized columnar events; materialize graph views. Evaluate SQLite/Parquet first, then dedicated graph databases only after scale benchmarks.

## Queries

Find all observed flows from a synthetic marker; enumerate unexplained device-triggered paths; compare two experiment subgraphs; retrieve every evidence artifact behind a claim.

## Scaling

Partition by experiment and process; use interval indexes for addresses, composite indexes for time/entity, bounded traversals, and streaming graph deltas.

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

