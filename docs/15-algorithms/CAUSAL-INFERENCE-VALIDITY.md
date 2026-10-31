# Causal inference validity

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Avoid confusing chronological order, observed data flow and experimentally established causal effect.

## Three evidence levels

Observed event: direct trace or instrumentation; inferred edge: model-based hypothesis; validated effect: controlled intervention with replicated outcomes and a documented counterfactual design.

## Experimental design

Use paired runs, fixed seeds, randomized scenario ordering when appropriate, environment fingerprinting, negative controls and repeat counts.

## Threats to validity

Hidden confounders, timing perturbation from instrumentation, missing PT packets, environment drift, false marker matches and emulator-model errors.

## Reporting

Publish effect size, uncertainty, number of runs, data exclusions, competing explanations and unresolved gaps. Never output a single unexplained confidence score.

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

