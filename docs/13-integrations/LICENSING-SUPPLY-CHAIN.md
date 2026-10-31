# Licensing, SBOM and supply-chain governance

> MCP-AADF v4 design proposal · Status: **not implemented** unless explicitly stated otherwise.

## Purpose

Assess legal and technical obligations of third-party research engines.

## Before adoption

Record upstream repository, version/commit, license, transitive dependencies, supported targets, maintenance status, and security disclosures.

## Reproducible builds

Pin dependencies and container digests; generate SBOM (CycloneDX or SPDX), sign releases, and verify source provenance.

## Isolation

Run third-party parsers/decoders on untrusted traces in least-privilege sandboxes with resource caps.

## Upgrade strategy

Use contract tests and a compatibility matrix; update one adapter at a time, with rollback support.

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

