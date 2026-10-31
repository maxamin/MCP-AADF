# Threat model and abuse cases

**Status:** design specification; not implemented.

## Assets
Operator authorization, privileged helper credentials, target identity, collected evidence, driver packages, policy decisions, model context, lab boundaries.

## Threat actors
Malicious target application, compromised MCP server, poisoned documentation, untrusted third-party driver, malicious collaborator and accidental operator error.

## Abuse cases
Prompt injection requesting broader scope; symlink race on allowlisted paths; confused deputy via inter-driver delegation; replay of approval tokens; tampered driver package; forged telemetry; exfiltration through report fields; unbounded device command loop.

## Mitigations
Pinned driver hashes, signed release metadata, target identity revalidation, no ambient credentials, capability grants with expiration, sandboxed workers, output redaction, egress controls, audit correlation, resource quotas and mandatory human review for state changes.

## Security tests
For each abuse case define entry point, preconditions, expected deny behavior, logging requirement and regression test. Run adversarial tests in CI using synthetic targets.

## Residual risks
Kernel vulnerabilities, hypervisor escapes, faulty hardware, compromised OS trust roots, model deception and incomplete telemetry remain outside any single MCP policy's guarantees.
