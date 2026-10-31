# Threat Model: Emulated Devices and Memory Markers

## Assets
Host integrity, physical device safety, protected process memory, experiment integrity, private data, trusted evidence, authorization grants, and driver isolation.

## Threats and controls
| Threat | Mitigation |
|---|---|
| Malicious device descriptor / protocol input | Parser hardening, fuzzing, length bounds |
| Unsafe simulated actuator action | Virtual-first execution, hardware interlock |
| Marker leakage into logs / external sinks | Synthetic-only markers, network isolation, output filtering |
| Arbitrary memory access | Owned fixtures, range allowlists, read/write quotas |
| Cross-driver confused deputy | Per-call policy checks, scoped grants |
| Untrusted MCP tool output injection | Structured parsing, trust labeling, no implicit execution |
| Trace forgery / timestamp manipulation | Evidence hashes, monotonic clocks, source provenance |
| False causal conclusions | Controlled experiments, repeated trials, confounder review |
| Resource exhaustion | CPU/memory/time limits, kill switch |
| Failed rollback | Snapshot verification and fail-closed quarantine |

## Explicit exclusions
No autonomous kernel patching, no protected enclave bypass, no covert persistence, no credential harvesting, and no unapproved physical-device interaction. Report limitations honestly.
