# Device emulation and hardware-in-the-loop

**Status:** design specification; not implemented.

## Backends
Use QEMU/Renode for virtualized peripherals, Linux USB gadget for supported USB test devices, virtual serial ports and network namespaces for protocol fixtures. Hardware-in-the-loop requires dedicated owned development boards and physical safety controls.

## Device model
Represent descriptors, capabilities, state machine, timing tolerances, error responses, protocol version and firmware metadata. Differentiate faithful emulation from an approximate simulator.

## Safety interlocks
Block actuator commands by default. Require power isolation, emergency stop, bus speed limits, physical supervision and explicit approval for firmware writes. Do not emulate credentials or trusted security devices to bypass authentication.

## Test plan
Enumerate device, compare descriptors, run harmless read-only probes, inject bounded synthetic errors, measure timing, record host driver response, restore baseline.

## Metrics
Protocol coverage, state transition coverage, response accuracy, timing deviation, reproducibility, crash rate and unexpected side effects.
