# MCP Interfaces for Behavioral Intelligence

These are proposed **application-level tool names**, not native MCP protocol methods.

| Tool | Side effect | Authorization |
|---|---|---|
| `device.model.inspect` | None | Target read |
| `device.scenario.validate` | None | Manifest read |
| `device.scenario.run` | Virtual device state | Lab + approval |
| `memory.marker.plan` | None | Fixture read |
| `memory.marker.plant_fixture` | Lab buffer write | Lab + approval |
| `memory.marker.events` | None | Evidence read |
| `execution.graph.query` | None | Graph read |
| `experiment.compare` | None | Evidence read |
| `experiment.rollback` | Fixture restoration | Lab scope |

## Common request envelope
```json
{
  "schema_version": "1.0",
  "request_id": "req-001",
  "target_id": "lab-vm-01",
  "experiment_id": "exp-001",
  "capability": "device.scenario.run",
  "policy_token_ref": "opaque-authorized-grant",
  "arguments": {"scenario_id": "serial-attach-test"}
}
```

## Common response envelope
```json
{
  "request_id": "req-001",
  "status": "completed",
  "evidence_ids": ["ev-001"],
  "warnings": [],
  "result": {"observed_transitions": 4}
}
```

## Enforcement
The host validates target, operator grant, capability, side effects, schema, expiry, and execution environment immediately before every action. Treat MCP tool outputs as untrusted. No privilege inheritance across drivers. Record denial as a first-class auditable event.
