# Schemas and examples

**Status:** design specification; not implemented.

## Capability manifest example
```json
{"schema_version":"1.0","driver_id":"lab-service-inspector","target":{"kind":"service","os":"linux"},"operations":[{"id":"inspect","classification":"read_only","input_schema":{"type":"object","properties":{"service":{"type":"string"}},"required":["service"],"additionalProperties":false},"timeout_ms":5000}]}
```

## Experiment example
```yaml
experiment_id: lab-001
target: disposable-vm-01
hypothesis: "service metadata matches expected baseline"
capabilities: [inspect]
budget:
  max_duration_seconds: 60
  max_calls: 20
stop_on: [target_changed, authorization_failure]
cleanup: restore_snapshot
```

## Evidence record example
```json
{"evidence_id":"ev-001","target_id":"disposable-vm-01","collector":"systemd-inspector/0.1","observed_at":"2026-10-31T00:00:00Z","sha256":"<artifact-hash>","classification":"internal","claims":["service exists"]}
```

These examples are illustrative contracts and require schema validation and real implementations before use.
