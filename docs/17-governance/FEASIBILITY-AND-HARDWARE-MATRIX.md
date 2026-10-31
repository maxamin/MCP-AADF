# Feasibility and hardware matrix

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Document realistic platform constraints, especially Intel PT and protected memory.

## CPU tracing

Intel PT requires compatible Intel CPU, PMU/kernel support and permissions; AMD systems need alternatives. ARM ETM depends on SoC/kernel exposure. Consumer phones rarely expose full privileged tracing.

## Memory

User-mode instrumentation cannot see arbitrary kernel/TEE/enclave memory. Debuggers and emulators operate only within their legitimate visibility and permission boundaries.

## Emulation

QEMU and Renode emulate selected devices, not every physical effect; HIL requires explicit device safety, power and bus limits.

## Resource profiles

8GB RAM machines should use streaming ingestion, small trace chunks, no heavyweight graph service by default, and remote optional runners for VM-heavy tests.

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

