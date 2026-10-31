# Cross-platform observability

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

A platform adapter model spanning Linux, Windows, Android and macOS without pretending feature parity.

## Linux

perf/Intel PT where supported, eBPF for kernel events, ptrace for scoped debugging, audit events and QEMU for emulation.

## Windows

ETW for system events, debugger APIs for authorized analysis, platform-specific hardware trace support only after capability probing.

## Android

ADB-based owned-device testing, Perfetto for traces, app-level instrumentation where permitted, hardware trace subject to kernel and device support.

## macOS

Instruments and DTrace where permitted, LLDB, virtualization frameworks; account for platform entitlement restrictions.

## Contract

Each platform declares support and gaps. Cross-platform normalized events must retain the original backend-specific evidence.

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

