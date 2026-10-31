# QEMU, PANDA and Renode integration

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Separate generic virtual machines, whole-system replay, and embedded device simulation.

## QEMU adapter

QMP for VM lifecycle, virtual device attachment, snapshots, guest agent in owned VMs, and trace event collection. Track guest image and device-model versions.

## PANDA adapter

Record/replay experiment runs and consume plugin events. Verify supported target architectures and PANDA plugin compatibility before scheduling experiments.

## Renode adapter

Load platform descriptions, scripts and firmware images; emit peripheral I/O, interrupts and virtual sensor telemetry with deterministic seeds.

## No universal equivalence

A USB controller in QEMU, an MCU peripheral in Renode and a physical device are different fidelity classes; tests must state what was modeled.

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

- https://www.qemu.org/
- https://github.com/panda-re/panda
- https://github.com/renode/renode
