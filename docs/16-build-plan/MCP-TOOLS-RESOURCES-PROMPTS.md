# MCP interface design

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Expose explicit, narrow tools and read-only resources rather than one generic privileged command.

## Tools

`capabilities.list`, `experiment.validate`, `experiment.start`, `experiment.cancel`, `trace.capture`, `trace.decode`, `graph.query`, `device.scenario.run`, `marker.create_lab`, `marker.observe_lab`, `evidence.export`. Every tool validates target scope and resource budgets.

## Resources

Immutable experiment manifests, capability reports, graph snapshots, artifact hashes, provenance chains and trace quality reports.

## Prompts

Analyst workflows can suggest next safe experiments but must not bypass authorization, approval, or device safety policies.

## Error taxonomy

`UNSUPPORTED`, `UNAUTHORIZED`, `TARGET_NOT_OWNED`, `RESOURCE_EXHAUSTED`, `TRACE_LOSS`, `PARTIAL_EVIDENCE`, `SCHEMA_MISMATCH`, `CANCELLED`, `REPLAY_DIVERGED`.

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

