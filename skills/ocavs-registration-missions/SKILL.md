---
name: ocavs-registration-missions
description: OCAVS vehicle registration, capability profiles, availability, reconciliation, and vehicle/fleet mission workflows. Load for fleet onboarding or mission lifecycle work.
---

# OCAVS Registration and Missions

## Specification Versions

This skill references **OCAVS** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load when implementing or reviewing CAV registration, capability reporting, assignment availability, resource reconciliation, vehicle-initiated missions, CCMS-initiated missions, or mission tasks.

## Key References

- [Registration and state types](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/03-data-types/03-02-registration.md), [mission types](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/03-data-types/03-03-missions.md)
- [Registration operations](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/04-operations/04-01-registration.md), [vehicle-initiated missions](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/04-operations/04-02-cav-missions.md), [CCMS-initiated missions](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/04-operations/04-03-ccms-missions.md)
- [CAV lifecycle](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/05-application/05-03-cav-lifecycle.md), [CCMS lifecycle](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/05-application/05-04-ccms-lifecycle.md)

## Scope

This skill covers the application relationship between a CAV and its central fleet system: registration and capabilities; operational and assignment availability; reconciliation of known resources; and mission authorization, updates, execution, cancellation, completion, and failure.

## Rules

- Use the operation definitions for initiator, permission, request fields, processed response, status, and result mapping.
- Treat vehicle registration, reported capability, operational state, assignment availability, and mission state as separate resources or concepts.
- Check feature-profile dependencies before accepting an operation that requires a capability.
- Follow the vehicle-initiated and CCMS-initiated mission flows independently; their authority and transition rules differ.
- Apply mission deadlines, revision and idempotency rules, command sequence behavior, and cancellation/completion outcomes exactly as specified.
- Use reconciliation rules after restart or restored connectivity. Do not infer mission completion from a transport acknowledgement.
- Preserve task-level state and mission-level state distinctions.
- Keep high-level mission orchestration within the protocol's safety boundary; never translate it into low-level actuator commands.

## Common Pitfalls

- Treating a vehicle's advertised capability as proof that a feature profile is enabled.
- Changing assignment availability without applying the specified policy and result.
- Applying a CCMS mission transition to a vehicle-originated mission.
- Recreating a mission after a timeout instead of resolving the original idempotent operation.
- Confusing mission authorization with transport identity or security credentials.
- Reporting a mission complete while required tasks or terminal conditions remain unresolved.
