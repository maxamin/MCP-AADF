# Taint, symbolic execution and fuzzing integration

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Build a research pipeline that combines observed marker propagation with bounded path exploration.

## Taint providers

Triton and DynamoRIO-based clients can produce dynamic taint observations in controlled binaries. A marker is a synthetic label, not a real credential.

## Symbolic providers

angr/Triton and Z3 can reason about path constraints. Enforce bounded execution, memory budgets and explicit timeouts.

## Fuzzing providers

AFL++ and libAFL consume coverage and crashes from isolated harnesses; kAFL/Nyx are advanced options for VM-based coverage and reset.

## Feedback loop

Prioritize unexplored graph regions; use differential execution and delta debugging to reduce triggering inputs; store reproducible minimal test cases.

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

