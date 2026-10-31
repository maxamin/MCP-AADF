# Research engine integrations

**Status:** design specification; not implemented.

## Reverse engineering
Adapters for Ghidra project metadata, symbol references, control-flow summaries, debugger breakpoints on owned processes, and binary diffs. Maintain versioned evidence and avoid claiming a decompiler reconstruction is original source.

## Fuzzing
Use coverage-guided fuzzers only on owned or explicitly authorized targets. Drivers produce typed harness specifications, seed corpus metadata, crash hashes, minimized reproducers and regression tests. Limit resource use and keep network effects sandboxed.

## Forensics
Acquire immutable evidence references, preserve timestamps and hashes, reconstruct timelines and distinguish findings from hypotheses.

## Post-compromise assessment
Model an explicitly granted test identity and enumerate accessible services, configuration, privilege boundaries and persistence artifacts. Use reversible simulations in lab fixtures; do not automate covert access, credential harvesting or stealthy persistence.

## Cloud and mobile
Use read-only IAM and configuration APIs for cloud, Android adb and package metadata on owned devices, and signed application test builds for instrumentation. Explicitly model platform sandbox restrictions.
