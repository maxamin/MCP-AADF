# Reproducible Experimental Design

## Run contract
Each run must specify `experiment_id`, hypothesis, independent/dependent variables, target image digest, authorized scope, intervention, control, seed, instrumentation, resource limits, expected observations, stopping rules, and cleanup.

## Experimental protocol
1. Snapshot the isolated environment.
2. Validate image digest and target identity.
3. Run control N times; record event and timing variance.
4. Run intervention N times using the same workload and controlled seeds.
5. Compare events, state transitions, graph edges and errors.
6. Triage divergence; minimize inputs where possible.
7. Restore snapshots and verify device and marker cleanup.
8. Publish a machine-readable evidence manifest and uncertainty notes.

## Metrics
- Event loss and timestamp skew.
- Device transition and protocol coverage.
- Marker source-to-sink precision and recall on ground-truth fixtures.
- Graph edge precision and evidence completeness.
- False-positive rate for causal inference.
- Median and tail execution overhead.
- Reproduction rate across machines and OS versions.

## Stop conditions
Out-of-scope target, unexpected external network traffic, host resource threshold, unsafe physical actuator state, unapproved memory access, failure to restore baseline, or policy denial.
