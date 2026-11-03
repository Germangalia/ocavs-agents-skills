---
name: ocavs-safety-environment
description: OCAVS operational design domains, geofences, operational/safety events, evidence references, and high-level control extensions. Load for safety boundary and environment-provisioning work.
---

# OCAVS Safety and Environment

## Specification Versions

This skill references **OCAVS** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load when working with operational design domain (ODD) resources, geofence sets/zones, safety events, collision reports, evidence references, vehicle reset, auxiliary actions, or vendor extensions.

## Key References

- [ODD and event types](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/03-data-types/03-09-odd-and-events.md)
- [ODD and geofence operations](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/04-operations/04-11-odd-geofencing.md), [event operations](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/04-operations/04-12-events.md), [control extensions](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/04-operations/04-13-control-extensions.md)
- [Core concepts and safe autonomy boundary](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/01-architecture/01-01-core-concepts.md), [application behavior](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/05-application/05-01-application-behavior.md)

## Rules

- Preserve the separation between remote high-level application commands and the vehicle's local safety/autonomy enforcement.
- Never generate steering, braking, throttle, drivetrain, actuator setpoints, or executable live trajectories from these operations.
- Apply ODD and geofence revisions, validity windows, geometry constraints, actions, and compliance outcomes exactly as defined.
- Treat safety/operational events as domain reports with their defined severity, category, timing, and evidence references; do not infer facts absent from the event payload.
- Apply evidence reference constraints without embedding raw media or unbounded artifacts in a message.
- Follow safety-command expiry, sequencing, authorization, and terminal result rules for reset and auxiliary actions.
- Keep vendor extension handling within declared extension types and validation behavior; unknown or invalid extension data must follow the specified outcome.

## Common Pitfalls

- Using geofence data as an implicit actuator command.
- Accepting malformed geometry or expired ODD/geofence resources.
- Treating an event acknowledgement as resolution of the underlying safety condition.
- Including raw media or personal data where only a bounded reference or minimized summary is allowed.
- Allowing vendor-specific fields to bypass schema, authorization, or safety checks.
