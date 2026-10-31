# Intel Processor Trace integration

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

An optional hardware control-flow observation backend for supported Intel processors. PT does not capture arbitrary data values or all memory accesses.

## Acquisition and decoding

Use Linux `perf` and the `intel_pt` PMU to acquire trace streams; decode with Intel libipt or supported perf decoders. Separate acquisition, sideband metadata (mmap, context switch, image identity), packet decode, and basic-block reconstruction. Trace gaps, packet loss, address-space changes, CPU migrations, and ASLR must be first-class outcomes.

## Event normalization

Emit `branch_observed`, `block_executed`, `trace_gap`, `image_mapped`, and `context_switch` events. Include CPU, thread, process namespace, image build ID, load offset, timestamp confidence, and raw trace reference. Resolve addresses only when the corresponding image and mapping are known.

## Capability negotiation

Probe `/sys/bus/event_source/devices/intel_pt`, kernel perf permissions, CPU model and hypervisor constraints. Fall back to software instrumentation or emulated traces; never claim Intel PT support from CPU brand alone.

## Proof of concept

Run two controlled binaries with distinct branch decisions; capture PT on a compatible host, reconstruct basic blocks, and compare against a compiler-instrumented ground truth. Report missing blocks and decode ambiguities.

## Risks and limitations

PT buffer overflow, timing effects, JIT/self-modifying code, privilege restrictions, trace confidentiality, and decoder mismatches can undermine fidelity. Restrict acquisition to explicitly authorized workloads.

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

## Research starting points

- https://github.com/intel/libipt
- https://docs.kernel.org/trace/intel_th.html
- https://perf.wiki.kernel.org/
