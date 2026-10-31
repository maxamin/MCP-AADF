# Implementation Backlog and Acceptance Gates

## Milestone M1: Observable fixture
- [ ] Build Rust event schema and append-only trace writer.
- [ ] Implement a purpose-built C/Rust process with known buffers and threads.
- [ ] Add stable IDs, monotonic timestamps, and trace export.
- [ ] Tests: schema round-trip, event ordering, event-loss detection.

## Milestone M2: Device behavior
- [ ] Implement a virtual serial device with Mealy state machine.
- [ ] Add deterministic attach/activity/disconnect scripts.
- [ ] Capture responses, timing, and driver-facing events.
- [ ] Tests: transition coverage, fixed-seed replay, teardown.

## Milestone M3: Memory markers
- [ ] Implement synthetic marker registry and TTL.
- [ ] Add in-process marker placement in approved buffers.
- [ ] Track copy and one reversible transform via instrumentation.
- [ ] Tests: known propagation, false-positive fixture, cleanup.

## Milestone M4: Graph + experiments
- [ ] Build observed/inferred/validated edge ontology.
- [ ] Implement baseline/intervention experiment runner.
- [ ] Add graph diff and evidence linkage.
- [ ] Tests: ground-truth graph precision, confounder scenario.

## Milestone M5: Algorithms
- [ ] Integrate coverage-guided fuzzing against virtual device parser.
- [ ] Implement delta debugging of failing synthetic sequences.
- [ ] Add temporal invariants and protocol inference prototype.
- [ ] Tests: reproducer minimization, safety assertion rejection.

## Definition of done
Documented contract, executable tests, measured performance, policy review, reproducible lab fixture, rollback, and no unsupported capability claims.
