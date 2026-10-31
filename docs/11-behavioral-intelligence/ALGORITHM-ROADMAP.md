# Algorithm Roadmap and Research Priorities

| Priority | Algorithm | Primary use | Validation |
|---|---|---|---|
| P0 | Finite-state / Mealy machines | Device activity | Transition coverage |
| P0 | Control/data-flow graphs | Execution structure | Known fixture edges |
| P0 | Happens-before | Concurrent event ordering | Race test fixtures |
| P0 | Differential execution | Stimulus response | Repeated A/B runs |
| P0 | Dynamic taint | Synthetic marker propagation | Known source-to-sink cases |
| P1 | Active automata learning (L*) | Protocol inference | Learned-vs-reference model |
| P1 | Coverage-guided fuzzing | Robustness testing | Coverage and crash reproducibility |
| P1 | Delta debugging | Minimize failing scenarios | Minimal reproducer |
| P1 | Program slicing | Explain observed outcomes | Slice relevance |
| P1 | Concolic execution | Explore constrained paths | New reachable paths |
| P1 | Temporal logic monitoring | Safety assertions | Invariant detection |
| P1 | Causal interventions | Validate graph edges | Repeated interventions |
| P2 | Vector clocks | Distributed causality | Partial-order accuracy |
| P2 | Partial-order reduction | Concurrency efficiency | State-space reduction |
| P2 | Bayesian updating | Hypothesis ranking | Calibration / Brier score |
| P2 | Change-point detection | Runtime shifts | Detection delay / false alarms |
| P2 | CEGAR | Refine abstract models | Counterexample quality |
| P3 | Graph neural networks | Anomaly ranking | Ground-truth precision and drift |

## Selection principles
Start with deterministic, interpretable methods; add statistical models only after obtaining labeled evaluation datasets. Preserve algorithm version, parameters, random seed, dataset provenance and uncertainty. No AI-generated hypothesis becomes a confirmed graph edge without test evidence.

## Roadmap
- Release A: event schema, FSM, baseline traces, graph projection.
- Release B: synthetic markers, object-level taint, differential replay.
- Release C: protocol learning, fuzzing, delta debugging, temporal assertions.
- Release D: concolic analysis, causal confidence calibration, distributed ordering.
- Release E: experimental graph learning and model drift monitoring.
