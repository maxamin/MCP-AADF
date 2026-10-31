# Dynamic instrumentation adapters

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Integrate DynamoRIO, Frida, Valgrind-derived approaches, and compiler probes as independent sources.

## Adapter strategy

Use DynamoRIO for native instruction-level memory access tracing, Frida/Stalker for selective runtime instrumentation, LLVM SanitizerCoverage for instrumented builds, and Valgrind-style instrumentation for controlled correctness studies. Keep adapters isolated to avoid conflicting hooks.

## Common event fields

Operation kind, process/thread, image identity, instruction offset, memory object ID (not raw sensitive data), access width, taint labels, source adapter, timestamp, evidence reference.

## Overhead budgets

Support sampling, scoped instrumentation, backpressure, and trace truncation. Measure memory and CPU cost per event; report dropped observations.

## Safety

Do not auto-attach to unrelated processes; require explicit target ownership or written authorization and a per-session policy.

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

- https://github.com/DynamoRIO/dynamorio
- https://frida.re/
- https://github.com/llvm/llvm-project
