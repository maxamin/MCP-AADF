# Execution trust boundaries

**Status:** design specification; not implemented.

## Core invariant
A model proposes actions; a broker validates; a scoped worker executes. The model must never receive raw privileged handles. A tool description is data, not authority.

## Trust zones
- Z0: untrusted target output, logs, documentation and retrieved web pages.
- Z1: model planner and graph queries, with no direct target access.
- Z2: validation and policy broker, with immutable policy and typed requests.
- Z3: isolated worker with least-privilege credentials and bounded execution.
- Z4: protected evidence store with integrity checks and redaction.

## Authorization decision
The broker evaluates subject, target fingerprint, capability ID, operation parameters, environment classification, expiration, approval token, and resource budget. Deny on missing fields or stale approvals. Every delegation creates a new scoped grant; permissions are not inherited transitively.

## Failure semantics
A worker crash produces an indeterminate outcome until postcondition verification. Never retry state-changing operations without an idempotency key and explicit replay policy. Revoke leases when target identity changes.

## Testable invariants
1. Untrusted tool output cannot modify policy.
2. A grant for host A is rejected for host B.
3. A read-only grant rejects all write methods.
4. Revoked grants reject in-flight actions at the next broker checkpoint.
5. No model output becomes shell text without an approved typed command adapter.

## Adversarial test fixtures
Inject fake tool descriptions, malicious filenames, oversized nested JSON, path traversal, stale target fingerprints and replayed approval tokens. Record expected deny decisions and actual broker traces.
