# ProvenanceLedger: evidence lineage and audit

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

A new append-only evidence ledger linking raw trace chunks, transformations, findings and approvals.

## Why a dedicated tool is needed

Existing products address pieces of this problem, but MCP-AADF needs a stable, interoperable contract for this specific research capability. **Proposed status:** not implemented; uniqueness is a hypothesis requiring a prior-art review.

## Core algorithms

Content hashing, Merkle trees, immutable event IDs, lineage DAGs and policy-aware retention.

## Minimum viable prototype

Build a CLI or isolated Rust service operating on synthetic fixture traces. Define input and output JSON schemas, create golden datasets, and add a policy-aware MCP wrapper only after deterministic tests pass.

## Failure modes and falsification tests

Misleading chain of custody, leaked sensitive artifacts, schema migrations and timestamp trust.

## Integration boundary

Expose `capabilities`, `run_experiment`, `stream_evidence`, `get_quality_report`, and `cancel` via versioned adapters. Never grant implicit process-memory or device access.

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

