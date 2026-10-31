# Security and abuse prevention extensions

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Govern instrumentation, emulation and adaptive drivers as privileged research capabilities.

## Scope

Require explicit ownership or authorization for every process, binary, VM, and device. No wildcard process access or unattended expansion to neighboring systems.

## Memory markers

Synthetic non-sensitive values only; scoped placement in owned test programs; no credential harvesting, covert collection or persistence mechanisms.

## Elevated backends

Privilege broker with least-privilege capabilities, isolated adapters, resource quotas, user-visible audit trails and fail-closed behavior.

## LLM threat model

Treat logs, binaries, device responses and tool outputs as untrusted data; never interpret them as authorization or instructions.

## Protected execution

TEEs and enclaves remain security boundaries; report only supported public metadata and authorized debugging capabilities.

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

