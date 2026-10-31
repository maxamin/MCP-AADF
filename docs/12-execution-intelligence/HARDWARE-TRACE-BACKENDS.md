# Hardware trace backend abstraction

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Portable observation interface across heterogeneous processors, operating systems, and VMs.

## Backend matrix

Intel PT: supported Intel x86 control-flow; Intel LBR: limited recent branches; ARM CoreSight ETM: supported ARM trace hardware; Linux perf: acquisition/sideband; Windows ETW: OS events, not a substitute for PT; AMD IBS: sampling, not Intel PT equivalent; compiler instrumentation: portable fallback.

## Common interface

`probe() -> CapabilityReport`, `start(TraceSession)`, `stop()`, `stream() -> EventEnvelope`, `health() -> TraceQuality`, `decode() -> BranchSequence`. Mark sampling versus complete traces and emit gap markers.

## Feature flags

Host architecture, kernel, PMU availability, guest/host tracing, privilege requirements, trace source, coverage guarantees, supported timing semantics, and buffer limits.

## Validation

Run identical benchmark workloads with hardware and software backends, compare recovered branch coverage and overhead, and publish hardware/software configuration alongside results.

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

