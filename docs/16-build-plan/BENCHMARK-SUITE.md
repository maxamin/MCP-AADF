# Benchmark suite and reproducibility

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Evidence-based acceptance metrics rather than aspirational performance claims.

## Workloads

CPU branch benchmark, synthetic multi-threading, memory copy/transform, device state machine, VM boot/attach, and large graph import.

## Metrics

Events/sec, decode MB/sec, overhead ratio, p95 latency, memory peak, dropped-event rate, block coverage precision/recall, marker propagation recall, replay divergence, graph query p95.

## Hardware matrix

Low-memory 8GB CPU-only development, midrange Intel PT host, ARM64 Android client, isolated VM runner. Clearly separate unsupported configurations.

## Artifact requirements

Pin binary hash, compiler flags, OS/kernel, CPU flags, tool versions, random seeds and trace capture policy. Publish raw and normalized fixtures.

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

