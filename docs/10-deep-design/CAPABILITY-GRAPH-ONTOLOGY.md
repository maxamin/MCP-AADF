# Capability graph ontology

**Status:** design specification; not implemented.

## Entity taxonomy
`Application`, `Executable`, `Process`, `Identity`, `Service`, `File`, `API`, `IPC`, `Device`, `Driver`, `MemoryMapping`, `VirtualMachine`, `Policy`, `Evidence`, `Observation`.

## Edge taxonomy
`EXECUTES_AS`, `EXPOSES`, `READS`, `WRITES`, `DEPENDS_ON`, `HOSTED_BY`, `CONNECTED_TO`, `OBSERVED_BY`, `REQUIRES_PERMISSION`, `ATTESTED_BY`. Every edge is directed and includes source evidence and scope.

## Observation model
Store asserted fact separately from inference. Each observation includes source ID, collector version, timestamp, target fingerprint, collection method, confidence, validity window and SHA-256 of source artifact. Never overwrite prior observations; create superseding revisions.

## Conflict resolution
When two sources disagree, preserve both and mark the edge disputed. Prefer independent observations over model guesses; do not silently promote confidence. A finding may cite multiple observations and an explicit inference rule.

## Graph queries
- Which writable configuration files are consumed by elevated services?
- Which devices are accessed by a given process?
- Which dependencies changed since baseline?
- Which claims are based only on inference?

## Storage
Start with SQLite tables for nodes, edges, observations, evidence and revisions. Index target, type, timestamp and provenance. Consider a graph database only after profiling query needs.
