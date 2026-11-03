---
name: ocavs-vehicle-operations
description: OCAVS energy, charging, health, variable monitoring, configuration, firmware/software, diagnostics, and logging operations. Load for fleet device-management workflows.
---

# OCAVS Vehicle Operations

## Specification Versions

This skill references **OCAVS** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load when implementing vehicle energy/charging, component inventory and health, variable monitoring, configuration changes, software or firmware lifecycle, diagnostic requests, or log delivery.

## Key References

- [Energy types](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/03-data-types/03-05-energy.md), [diagnostic types](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/03-data-types/03-06-diagnostics.md), [monitoring/configuration types](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/03-data-types/03-07-monitoring.md), [firmware/software types](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/03-data-types/03-08-firmware-software.md)
- Operations `04-operations/04-06-energy.md` through `04-operations/04-10-diagnostics.md` in the [OCAVS specification](https://github.com/Germangalia/OCAVS/tree/v0.1.0/ocavs-specification/04-operations)
- [General limits and defaults](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/appendix/D-limits-defaults.md)

## Domain Rules

- **Energy and charging:** follow charging-session states and permitted start/control actions. Report energy values with their defined units and direction.
- **Health and inventory:** distinguish component inventory, operational state, health observations, maintenance urgency, and diagnostic trouble codes.
- **Monitoring and configuration:** check variable mutability, requested apply mode, monitor definition/trigger, result type, and reporting rules before applying changes.
- **Firmware/software:** validate artifact metadata, signature, prerequisites, install policy, and operation state before reporting an update result. Do not treat artifact delivery as successful installation.
- **Diagnostics/logging:** honor requested detail, delivery mode, limits, authorization, and terminal result. Keep diagnostic data and external file transfer semantics separate.
- Use each operation's idempotency, expected revision, status mapping, asynchronous execution, and response-presence rules.
- Do not execute low-level vehicle control through configuration or maintenance operations.

## Common Pitfalls

- Treating a requested update as installed before the vehicle reports the defined terminal state.
- Treating energy source state as the same as battery health or charging state.
- Applying a configuration variable without checking mutability and apply policy.
- Assuming an empty diagnostic result means the request failed.
- Sending large diagnostic or firmware bytes inline instead of using the specified finite-transfer flow.
- Reusing a result enum or status code from a different operation family.
