# OCAVS Agents & Skills

[![skills.sh](https://skills.sh/b/Germangalia/ocavs-agents-skills)](https://skills.sh/Germangalia/ocavs-agents-skills)

A focused knowledge base for AI agents that design, implement, integrate, document, and validate systems using the **Open Cooperative Vehicle Architecture (OCVA)**, with an emphasis on the **Open Cooperative Autonomous Vehicle Server (OCAVS)** protocol.

This repository provides reusable skills and role-based agent instructions. It contains no protocol runtime or application implementation.

## Repository Structure

```text
.agents/
├── agents/       # Role-based agent instructions (AGENT.md)
└── skills/       # Reusable skill instructions (SKILL.md)

README.md
skills-lock.json # Skills CLI lockfile for the included skills
```

## Protocol Scope

OCAVS defines vehicle-to-server application and fleet/device management workflows. The OCAVS-specific skills in this repository cover vehicle registration and missions, supervision and telemetry, vehicle operations, and safety/environment behavior.

Some shared skills also cover concepts that apply across OCAVS, OCAVM (vehicle-to-vehicle and vehicle-to-infrastructure coordination), and OCAVI (platform-to-platform service interoperability). Use each protocol's own message identifiers, data types, permissions, profiles, status codes, and lifecycle rules; do not assume that a rule in one protocol applies to another.

The skills reference these specification release tags:

| Specification | Version tag | Source |
|---|---|---|
| OCAVS | [`v0.1.0`](https://github.com/Germangalia/OCAVS/tree/v0.1.0) | Vehicle-to-server application and fleet/device management |
| OCAVM | [`v0.1.0`](https://github.com/Germangalia/OCAVM/tree/v0.1.0) | Vehicle-to-vehicle and vehicle-to-infrastructure coordination |
| OCAVI | [`v0.1.0`](https://github.com/Germangalia/OCAVI/tree/v0.1.0) | Platform-to-platform service interoperability |

For normative requirements, consult the versioned specification source. Specification files are authoritative; skills and checklists provide guidance and planning support. When updating the skills, check the source repositories' release tags and keep these version references current.

## Skills

Skills are focused knowledge units that agents can load for relevant protocol work.

| Skill | Coverage |
|---|---|
| `ocavs-registration-missions` | Vehicle registration, capability profiles, availability, reconciliation, and vehicle/fleet mission workflows |
| `ocavs-supervision-telemetry` | High-level supervision, safe-stop behavior, sensor streams, telemetry flow control, perception metadata, and data acquisition |
| `ocavs-vehicle-operations` | Energy, charging, health, variable monitoring, configuration, firmware/software, diagnostics, and logging |
| `ocavs-safety-environment` | Operational design domains, geofences, operational/safety events, evidence references, and high-level control extensions |
| `ocva-foundation` | Scope, terminology, roles, deployment, profiles, and protocol boundaries across OCAVS, OCAVM, and OCAVI |
| `ocva-data-types` | Canonical scalar, object, enum, time, unit, identity, and geospatial representations |
| `ocva-message-semantics` | Request/response processing, idempotency, revisions, ordering, deadlines, and application lifecycles |
| `ocva-security-privacy` | Validation, authorization, privacy, secure-connectivity assumptions, and external-transfer constraints |
| `ocva-conformance` | Conformance classes, status catalogs, state-machine requirements, examples, limits, and evidence |
| `ocva-spec-authoring` | Normative document ownership, requirement language, repository conventions, examples, and release discipline |

**Total: 10 skills.**

## Agents

Agent definitions combine skills into task-focused responsibilities and outputs.

| Agent | Role |
|---|---|
| `protocol-architect` | Selects protocols, roles, profiles, normative owners, and deployment boundaries |
| `state-contract-engineer` | Designs typed message contracts, validators, idempotency, ordering, and state transitions |
| `security-privacy-engineer` | Reviews validation, authorization, privacy, and sensitive-data handling |
| `ocavs-vehicle-operations-developer` | Implements and reviews OCAVS registration, missions, supervision, telemetry, device management, diagnostics, and safety workflows |
| `integration-specialist` | Designs and troubleshoots handoffs across OCAVS, OCAVM, and OCAVI |
| `conformance-test-engineer` | Turns normative requirements into traceable positive, negative, lifecycle, security, and recovery tests |
| `documentation-release-writer` | Authors and reviews protocol documentation, examples, checklists, and release materials |

**Total: 7 role-based agents.**

## Use the Knowledge Base

1. Identify the protocol, operation, endpoint roles, profile, and specification version relevant to the task.
2. Load the matching instructions from `.agents/agents/` when a specialized role is useful.
3. Load the relevant skills from `.agents/skills/`. Begin with shared foundation guidance and add the applicable data-type, message-semantics, security, conformance, or OCAVS operation skill.
4. Check the selected protocol's versioned normative specification for the operation and type definitions.
5. Preserve protocol boundaries and report gaps rather than inventing behavior the specification does not define.

For OCAVS vehicle/fleet work, select the registration/missions, supervision/telemetry, vehicle-operations, or safety/environment skill according to the feature area. For cross-protocol work, begin with `ocva-foundation` and consult the relevant shared skills.

## Local Usage

Clone the repository:

```bash
git clone https://github.com/Germangalia/ocavs-agents-skills.git
cd ocavs-agents-skills
```

Configure your agent runtime to load skills from `.agents/skills/` and, if supported, role instructions from `.agents/agents/`.

## Repository Scope and Limitations

This checkout contains **10 skill definitions**, **7 role-based agent definitions**, and a lockfile with hashes for all 10 included skills. It does not contain the protocol specifications themselves or a runtime implementation. Skills currently live under `.agents/skills/`; there is no separate registry-facing `skills/` directory in this checkout.

Some agent definitions refer to OCAVM skill identifiers that are not included in this repository. Those references are not available local skills and are not included in the skill count above.

## License

No license is currently declared in this repository.
