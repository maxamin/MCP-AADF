# Future tools atlas: missing capabilities

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

A catalog of proposed components that are not assumed to exist as ready-made products.

## Novelty classes

`integration`: existing technology with adapter; `adaptation`: substantial fork/plugin; `new-tool`: a missing cross-domain capability; `research`: unproven feasibility.

## New-tool candidates

TraceFuse (multi-backend event fusion), MemoryBeacon (synthetic marker propagation), DeviceChronicle (behavioral replay), CausalGraphLab (intervention-aware execution graph), BoundaryOracle (privilege-boundary verifier), DriverForge (capability-scoped driver synthesis), FidelityMeter (emulation fidelity), TraceGapInspector (missing evidence), ExperimentCompiler (scenario to isolated run), ReplayProof (reproducibility verifier), ProtocolCartographer (state machine inference), ProvenanceLedger (tamper-evident evidence).

## Prioritization

Rank by research impact, integration readiness, testability, hardware availability, security risk, maintenance cost, and evidence value; do not equate ambitious ideas with near-term feasibility.

## Guardrails

No automatic unauthorized access, stealth persistence, privilege escalation, enclave bypass, or real-world exploitation. Unsafe experiments run only in controlled and authorized laboratories.

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

