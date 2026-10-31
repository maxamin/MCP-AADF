# Algorithm research roadmap

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

A staged research backlog balancing demonstrable engineering with exploratory methods.

## P0 deterministic core

Interval trees for mappings; DAG event stores; Lamport/vector clocks where appropriate; CFG path matching; streaming joins; deterministic finite state machines; content-addressed provenance; simple differential trace alignment.

## P1 advanced methods

Dynamic taint propagation; program slicing; concolic execution; active automata learning; coverage-guided fuzzing; delta debugging; partial-order reduction; temporal logic monitoring.

## P2 probabilistic methods

Bayesian evidence updates with calibrated priors; hidden Markov models for partially observed device state; change-point detection; probabilistic automata; causal intervention design.

## P3 research frontier

Graph neural networks only with labeled datasets and baselines; counterfactual execution models; causal representation learning; automated hypothesis search; abstract interpretation refinement.

## Evaluation

For every algorithm: define baseline, synthetic ground truth, held-out scenarios, precision/recall, runtime and memory cost, robustness to missing observations, and falsification criteria.

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

