# Memory forensics and TEE boundaries

**Status:** design specification; not implemented.

## Memory scope
Separate virtual mappings, file-backed pages, anonymous pages, kernel dumps, hypervisor snapshots, device memory and TEE metadata. These have different access and reliability models.

## Read-only workflow
Identify owned test process -> collect mapping metadata -> classify protections -> select allowlisted region -> bounded read through debugger -> hash and redact result -> verify target identity unchanged.

## Laboratory write fixture
Only write a known test variable in a purpose-built process. Require a test manifest with expected address range, exact byte count, original value hash, snapshot, authorization and rollback verification. No arbitrary cross-process writes or kernel patching.

## TEE limitations
Intel SGX, TDX, AMD SEV-SNP and TrustZone enforce distinct boundaries. An OS administrator or hypervisor may be unable to read protected contents. Support attestation verification, configuration inspection and development/debug enclaves only; report inaccessible content explicitly.

## Evidence handling
Do not place raw secrets or bulk dumps into LLM context. Store encrypted, access-controlled artifacts and pass references plus redacted summaries. Record acquisition method, consent scope and chain of custody.
