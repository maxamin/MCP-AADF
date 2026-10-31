# Ghidra static intelligence bridge

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Use Ghidra as a static analysis provider, not as the sole authority about runtime behavior.

## Export contract

Binary hash, architecture, image base, function entry, basic-block spans, call edges, imports, symbols, confidence, analysis version.

## Address reconciliation

Normalize ASLR via module mapping and image-relative offsets; separate speculative decompiler edges from runtime-observed edges.

## Change tracking

Reanalysis of a binary produces versioned graph deltas. Never silently reuse stale offsets after a build change.

## Demonstration

Compile a small sample with symbols and stripped symbols, compare static coverage to PT and instrumentation traces.

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

## Research starting points

- https://github.com/NationalSecurityAgency/ghidra
