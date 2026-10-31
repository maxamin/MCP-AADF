# Integration catalog and decision matrix

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Candidates are research leads, not claims of verified current compatibility. Integrate via bounded adapters, never a giant shared runtime.

## Priority zero

Intel libipt + perf (hardware trace), Ghidra (static analysis), DynamoRIO (memory instrumentation), QEMU (device emulation), Capstone/Zydis/Intel XED (instruction decoding), OpenTelemetry (telemetry export).

## Priority one

Frida (runtime hooks), PANDA (whole-system replay), Renode (embedded emulation), Triton (taint/symbolic), angr (program analysis), BCC/libbpf (kernel observability), Z3 (constraints), AFL++/libAFL (coverage testing).

## Priority two

kAFL/Nyx (PT-assisted VM fuzzing), rr (deterministic Linux replay where supported), CRIU (checkpoint experiments), Volatility 3 (memory forensics), YARA-X (content classification), Syzkaller (kernel test research), Qiling (emulation research), OpenOCD (embedded debugging).

## Evaluation rubric

Score licensing, supported OS/CPU, maintenance status, API stability, security boundary, reproducibility, runtime overhead, binary size, build complexity, community, and ability to operate without root.

## Integration boundaries

Out-of-process adapters use versioned IPC. GPL/AGPL and plugin compatibility require legal review; do not assume all code can be statically linked into a proprietary core.

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

