# In-Memory Honeytokens and Synthetic Marker Intelligence

## Purpose
Place uniquely identifiable **synthetic, non-secret** markers into designated buffers of instrumented test applications. Observe reads, copies, transformations, and sinks to understand data-flow paths. Never plant real credentials, extract third-party memory, or use unapproved cross-process writes.

## Marker lifecycle
`ALLOCATED -> PLANTED -> OBSERVED -> PROPAGATED | TRANSFORMED | EXPIRED -> RETIRED`. Each marker is bound to experiment ID, process identity, permitted buffer range, TTL, classification, and cleanup routine. Prefer marker placement by an in-process test harness rather than external memory injection.

## Event model
```json
{
  "schema_version": "1.0",
  "experiment_id": "exp-001",
  "marker_id": "synthetic-001",
  "process_id": "owned-fixture",
  "thread_id": "worker-1",
  "event": "copy",
  "source_object": "input_buffer",
  "destination_object": "work_buffer",
  "timestamp_monotonic_ns": 1542089000,
  "evidence": "instrumented-observation"
}
```

## Detection strategies
- Exact marker matching for direct copies; avoid treating it as full taint tracking.
- Instrumented object-level taint propagation across known operations.
- Dynamic binary instrumentation for fine-grained traces in disposable processes.
- Differential tests with marker absent/present to identify changed paths.
- Static slicing to identify potential unobserved routes.

## Limitations
Encoding, hashing, encryption, compression, pointer aliasing, optimized code, sampling, races, and uninstrumented boundaries may hide flows. A detected marker is evidence of reachability, not necessarily evidence of malicious access. A missing marker is not evidence of absence.

## Privacy and safety
Synthetic markers only; deny-list protected processes; memory ranges allowlisted; maximum bytes, duration, and retention; redaction before export. All modifications occur in controlled fixtures and require rollback validation.

## Acceptance tests
Detect direct copy and a known transform; do not falsely report unrelated buffers; demonstrate cleanup and TTL expiration; reject unauthorized process and range.
