# Privacy and data governance

**Status:** design specification; not implemented.

## Data classification
Public, internal, confidential and restricted. Memory dumps, credentials, private communications and personal data default to restricted.

## Collection minimization
Collect metadata rather than contents where possible. Redact before sending data to language models. Require explicit justification for raw memory or traffic capture.

## Retention
Per-project retention policy, deletion schedule and evidence hold process. Track derived artifacts to enable deletion propagation.

## Access
Role-based read access plus case-scoped authorization. Separate report readers from raw evidence custodians. Log access to restricted artifacts.

## Integrity
Hash artifacts at collection and export; preserve original bytes and metadata. Treat LLM summaries as derived, non-authoritative material.
