# Device state inference and conformance

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Infer device behavior without conflating simulated observations with physical truth.

## Baseline

Explicit hierarchical finite-state machines and timed automata for known devices.

## Learning

L* style active automata learning for resettable test targets; probabilistic transitions for noisy sensors; model-based conformance testing.

## Experiments

Use synthetic USB-like attach/detach, request/response, timeouts and fault injections. Require a safety allowlist for real hardware.

## Metrics

Transition coverage, distinguishing-sequence length, model complexity, timing error and behavioral mismatch rates.

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

