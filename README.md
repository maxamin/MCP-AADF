# MCP-AADF Documentation

> MCP-AADF documentation | Status: proposed design, not validated implementation.

An evidence-driven, policy-constrained architecture for adaptive software and device drivers. This is a design documentation repository; it does not claim that described capabilities are implemented.

## Start here

Read [the white paper](WHITEPAPER.md), [architecture](ARCHITECTURE.md), [scope](docs/00-governance/SCOPE.md), and [roadmap](docs/08-delivery/ROADMAP.md).

## Documentation map

- [Governance](docs/00-governance/SCOPE.md)
- [Architecture](docs/01-architecture/COMPONENTS.md)
- [MCP and drivers](docs/02-drivers/DRIVER-SPEC.md)
- [Research engines](docs/03-research/REVERSE-ENGINEERING.md)
- [Security](docs/04-security/THREAT-MODEL.md)
- [Experiments](docs/05-experiments/EXPERIMENT-DESIGN.md)
- [Engineering](docs/06-engineering/DEVELOPMENT.md)
- [Operations](docs/07-operations/DEPLOYMENT.md)
- [Delivery](docs/08-delivery/ROADMAP.md)
- [Appendices](docs/09-appendices/GLOSSARY.md)

## Operating principle

Observation → evidence → hypothesis → isolated experiment → validation → capability registration. MCP provides interoperability, not authority. Default to read-only operations and deny unsupported actions.

## Non-goals

No unrestricted memory access, kernel patching, stealth persistence, automated exploitation of unapproved systems, credential harvesting, or bypass of enclave protections.

## Documentation conventions

MUST/SHOULD/MAY indicate normative strength. Every example is illustrative until an integration test verifies it. Record evidence and version for every capability.



## Deep design companion

See [Deep engineering specifications](INDEX.md#deep-engineering-specifications) for execution boundaries, typed driver ABI, capability ontology, evidence pipelines, memory/TEE limitations, device emulation, experiment lifecycle, and release gates. These are design artifacts, not completed implementations.


## v3 extensions

The `docs/11-behavioral-intelligence/` directory adds device activity emulation, in-memory synthetic honeytokens, causal execution graphs, algorithm priorities, experiment design, MCP contracts, threat models, and an implementation backlog. These are research designs, not implemented software.

## v4 research expansion

New documentation covers hardware tracing (Intel PT/libipt/perf), instrumentation, Ghidra, QEMU/PANDA/Renode, causal execution graphs, synthetic memory markers, algorithm research, and a **future tools atlas** separating existing integrations from proposed new software. Start at [v4 index](V4-INDEX.md). The architecture is a proposal; no described integration is represented as working unless verified independently.
