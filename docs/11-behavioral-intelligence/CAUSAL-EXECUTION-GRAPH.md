# Causal Execution Graph and Evidence Ontology

## Graph model
Nodes: process, thread, instruction site, function, memory object, device, driver, service, event, experiment, observation, hypothesis, security boundary. Edges: calls, reads, writes, sends, receives, maps, depends_on, happens_before, inferred_causes, validated_causes.

Every edge stores `evidence_ids`, `source`, `time_interval`, `run_id`, `confidence_method`, and `status` (`observed`, `inferred`, `experimentally_validated`). Do not equate temporal order with causality.

## Causal procedure
1. Define outcome and intervention before running experiments.
2. Record a baseline trace with synchronized monotonic timestamps.
3. Change one variable in a disposable clone; hold other factors constant.
4. Repeat runs across controlled seeds; quantify variance.
5. Compute trace/graph differences and investigate confounders.
6. Promote an inferred causal edge only after successful reproducible intervention.

## Concurrency
Use Lamport clocks for coarse ordering, vector clocks for distributed partial orders, and happens-before relations for threads. Record unknown ordering explicitly. Consider partial-order reduction for equivalent schedules.

## Storage
Use SQLite for event/evidence metadata and a graph projection for traversal. Keep immutable raw traces separate from materialized graph views. Content-hash evidence and maintain source-to-edge lineage.

## Queries
- Which observed events preceded a specific buffer copy?
- Which device state changes consistently precede a service transition?
- Which trust boundary has no directly observed authorization evidence?
- What changed between baseline and intervention runs?

## Evaluation
Precision of known causal links, graph completeness, evidence provenance, time-alignment error, and reproducibility. Use synthetic ground-truth fixtures before real applications.
