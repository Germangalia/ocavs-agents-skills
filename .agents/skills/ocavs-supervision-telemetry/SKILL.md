---
name: ocavs-supervision-telemetry
description: OCAVS high-level supervision, safe-stop behavior, bounded sensor streams, telemetry flow control, perception metadata, and data acquisition. Load for live operational monitoring workflows.
---

# OCAVS Supervision and Telemetry

## Specification Versions

This skill references **OCAVS** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load for supervisory directives, safe-stop commands, sensor stream control, telemetry publication, flow control, perception metadata, or acquisition setup and reporting.

## Key References

- [Supervision and telemetry types](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/03-data-types/03-04-supervision.md)
- [Supervision operations](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/04-operations/04-04-supervision.md), [telemetry operations](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/04-operations/04-05-telemetry.md)
- [Application behavior](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/05-application/05-01-application-behavior.md), [limits and defaults](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/appendix/D-limits-defaults.md)

## Rules

- Apply only the high-level supervisory commands and result states defined by the operation contract.
- Honor command sequence, expiry/deadline, authorization, and local safety enforcement requirements.
- A safe-stop command requests a defined safety response; it is not a direct brake/steering/throttle setpoint.
- Treat sensor stream acceptance, active streaming, flow-control changes, stop reasons, and terminal state as separate lifecycle stages.
- Respect negotiated limits and flow-control feedback for telemetry. Do not assume unlimited rate, payload size, or retention.
- Keep raw/high-volume media and continuous high-rate data out of ordinary application payloads. Use only the finite, authorized transfer/acquisition mechanisms the specification defines.
- Preserve timestamp, sample sequence, sensor identity, quality, and error metadata when reporting telemetry.
- Follow acquisition definitions, triggers, filters, delivery modes, governance constraints, and terminal result requirements.

## Common Pitfalls

- Treating a structured sensor stream as permission to transport arbitrary raw media.
- Ignoring flow-control instructions or sending beyond a declared limit.
- Treating a received command as proof that execution completed.
- Allowing remote supervisory behavior to bypass the vehicle's local safety logic.
- Confusing data acquisition state with the state of a live telemetry stream.
- Omitting sample errors or data-quality indicators when a reading is partial or unavailable.
