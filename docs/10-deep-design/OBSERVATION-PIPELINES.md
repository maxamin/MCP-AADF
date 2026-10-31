# Observation pipelines

**Status:** design specification; not implemented.

## Collection layers
Static: executable headers, imports, packages, documentation. Runtime: process and service metadata, OS telemetry, API observations. Hardware: enumerated device descriptors, permitted debug metadata. Evidence must identify which layer produced it.

## Linux backend
Use procfs, systemd/DBus, package metadata, eBPF tracepoints where available, and debug tools on owned processes. Handle kernel lockdown, namespaces, Yama restrictions, missing symbols and dropped events explicitly.

## Windows backend
Use documented service APIs, Event Logs, ETW, PE parsing, and approved debugging interfaces. Handle access denied, PPL, architecture mismatches and changing process IDs.

## Normalization
Timestamp in UTC with monotonic sequence where possible. Resolve process identity with PID plus start time and host fingerprint, not PID alone. Track collector loss counters and sampling rates.

## Quality gates
Each collector must expose permissions, failure modes, expected overhead, test fixtures, sensitive-data classification and provenance. Never interpret absence of an event as proof of absence when coverage is incomplete.
