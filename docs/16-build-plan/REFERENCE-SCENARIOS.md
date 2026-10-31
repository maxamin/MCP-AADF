# Reference end-to-end scenarios

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Concrete experiments demonstrating differentiated functionality.

## Scenario A: branch choice

Two deterministic user-owned binaries; capture control flow via compiler instrumentation or PT; align with Ghidra CFG; emit observed graph and quality report.

## Scenario B: memory marker

Insert synthetic marker in an owned test process; copy and transform through known functions; compare instrumented ground truth to propagated labels.

## Scenario C: virtual device

QEMU virtual device attach/detach and fault sequence; record process and I/O events; replay with same seed and compare timelines.

## Scenario D: controlled intervention

Run with and without a synthetic device event; measure path differences across repetitions; label causal claim provisional until confounders are addressed.

## Scenario E: backend fallback

Disable Intel PT, verify capability report and software backend, and prove no silent degradation of trace fidelity classification.

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

