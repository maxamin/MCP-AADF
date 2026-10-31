# Performance and scalability

**Status:** design specification; not implemented.

## Budgets
Measure per-operation CPU time, peak RSS, I/O bytes, response latency, evidence size and worker startup overhead. Establish baseline on a pinned reference machine.

## Scheduling
Bound concurrent workers per host and per driver. Apply backpressure to telemetry collectors; surface dropped-event counters. Never drop authorization decisions or final operation outcomes.

## Caching
Cache static metadata keyed by executable hash and driver version. Invalidate dynamic capability data on target restart, process identity change, permission change or expiry.

## Isolation cost
Benchmark process sandbox, container and VM isolation separately. Do not optimize away privilege boundaries to improve latency.

## Capacity tests
Run 1, 10, 100 and 1000 synthetic observations; measure graph ingest, query p95, disk growth, failure recovery and redaction overhead.
