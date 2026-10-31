# Intel PT + libipt + perf integration RFC

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Specify capture, decode, sideband ingestion and recovery with measurable milestones.

## Modules

`pt-probe`, `pt-recorder`, `pt-sideband`, `pt-decoder`, `pt-symbolizer`, `pt-coverage`, `pt-quality`. Each has a stable message contract and integration tests.

## Stages

Stage A: manual perf capture; B: decoder output normalized; C: process/thread mapping; D: CFG alignment; E: streaming backpressure; F: differential run comparison.

## Fallback

If PT is unavailable, continue with compiler coverage or DynamoRIO, marking results as a different fidelity class.

## Failure conditions

Missing PMU, kernel permission denied, trace loss, unsupported packet, mapping ambiguity, version mismatch, or resource exhaustion must generate explicit error codes.

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

