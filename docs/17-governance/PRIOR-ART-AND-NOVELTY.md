# Prior art and novelty register

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Separate what is existing research, what needs adaptation, and what would be genuinely new.

## Already exists

Hardware branch tracing, binary instrumentation, whole-system replay, symbolic execution, fuzzing, state machine learning and telemetry systems.

## Integration novelty

Evidence-linked interoperability across PT, memory labels, device stimuli and static graphs under MCP with authorization and provenance.

## Research novelty candidates

Cross-backend evidence completeness; causal validity grading; emulation fidelity scoring; autonomous but policy-constrained experiment planning.

## Review protocol

Before claiming novelty, search academic literature, upstream tools and patents; record nearest prior art, gap, falsifiable hypothesis and competing approaches.

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

