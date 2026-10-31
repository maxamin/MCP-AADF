# Risk register v4

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

A prioritized risk register for hardware trace, memory observation and autonomous experiments.

## High: scope explosion

Mitigation: five-phase roadmap, vertical slices, hard interface contracts, no new backend without an end-to-end test.

## High: incorrect causal claims

Mitigation: observed/inferred/validated types, trace-gap accounting, paired controls and replication.

## High: unsafe privileged access

Mitigation: brokered capabilities, explicit target allowlists, lab-only mutation, security review and auditable approvals.

## Medium: platform fragmentation

Mitigation: capability negotiation and fallback fidelity labels, rather than pretending cross-platform equivalence.

## Medium: licensing conflicts

Mitigation: dependency/license registry and isolated process adapters.

## Medium: data explosion

Mitigation: bounded trace retention, compression, sampling with explicit labels, and tiered storage.

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

