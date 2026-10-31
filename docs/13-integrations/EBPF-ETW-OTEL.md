# eBPF, ETW and OpenTelemetry adapters

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Collect host events and export standardized telemetry while preserving raw evidence.

## Linux eBPF

Use libbpf/BCC where supported to observe scheduler, process, file and device events with minimal scoped data capture.

## Windows ETW

Collect selected kernel/application providers with documented permissions and buffering limitations.

## OpenTelemetry

Export spans/metrics/logs with correlation IDs, but retain the native event schema for precise execution semantics.

## Privacy

Default to hashes, object IDs and metadata rather than full memory payloads; document retention and redaction.

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

