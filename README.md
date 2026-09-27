# AuroraWatch-1 Ground Segment Cybersecurity Assessment

🇺🇸 English | [🇧🇷 Português](./README.pt-BR.md)

Fictional educational cybersecurity assessment of the Ground Segment and Mission Operations Center of a simulated Low Earth Orbit (LEO) Earth-observation mission.

## Important Disclaimer

AuroraWatch-1 is a fictional mission created exclusively for space cybersecurity study, training, and portfolio purposes.

This project does not represent an operational satellite, organization, customer, real security assessment, penetration test, compliance audit, or real mission architecture.

This project is not affiliated with NIST, SPARTA, The Aerospace Corporation, CCSDS, NASA, ESA, AEB, or any other organization mentioned in the references.

No testing is performed against real systems, third-party infrastructure, or production environments.

## Objective

This project applies publicly available cybersecurity references to a fictional space mission, focusing on:

- Ground Segment;
- Mission Operations Center (MOC);
- operator workstations;
- ground-station interfaces;
- operator and administrator access control;
- telemetry and telecommand workflows;
- third-party dependencies;
- threat modeling;
- risk assessment;
- security monitoring, detection, and incident response.

The objective is to connect Blue Team, DFIR, critical-environment security, OT/ICS, and space-operations concepts in a reproducible and safe scenario.

## Current Scope

The current scope includes:

- operator workstations;
- Mission Operations Center systems;
- mission-control servers;
- telemetry processing;
- mission-data and telemetry storage;
- telecommand workflows;
- ground-station gateway;
- identity, authentication, and privileged access;
- security monitoring, logging, and alerting;
- a fictional third-party ground-station provider interface;
- satellite simulation;
- configuration baseline services;
- backup and recovery services;
- time synchronization;
- network-security controls;
- synthetic security events, logs, alerts, and assessment evidence generated within the isolated laboratory.

Detailed scope information is documented in [docs/01-mission-and-scope.md](./docs/01-mission-and-scope.md).

## Architecture Overview

The current logical architecture is available in multiple formats:

- [Architecture Overview — PNG](./docs/architecture/architecture%20Overview.png);
- [Architecture Overview — SVG](./docs/architecture/Architecture%20Overview.svg);
- [Architecture Overview — Brazilian Portuguese JPG](./docs/architecture/Architecture%20Overview-ptbr.jpg);
- [Editable draw.io source](./docs/architecture/Architecture%20Overview.drawio).

The architecture overview shows the main zones, assets, mission-operation flows, telecommand and telemetry paths, security-event collection, monitoring, and cross-cutting services.

## Documentation

### Mission and architecture

- [Mission and Scope — English](./docs/01-mission-and-scope.md);
- [Mission and Scope — Português](./docs/01-mission-and-scope.pt-BR.md);
- [System Architecture — English](./docs/02-system-architecture.md);
- [System Architecture — Português](./docs/02-system-architecture.pt-BR.md).

### Assets and flows

- [Asset Inventory — English](./docs/03-asset-inventory.md);
- [Asset Inventory — Português](./docs/03-asset-inventory.pt-BR.md);
- [Data Flows and Trust Boundaries — English](./docs/04-data-flows-and-trust-boundaries-en-US.md);
- [Fluxos de Dados e Limites de Confiança — Português](./docs/04-data-flows-and-trust-boundaries-pt-BR.md).

## Study Methodology

The project is being developed progressively:

```text
Mission and scope
        ↓
System architecture
        ↓
Asset inventory
        ↓
Data flows and trust boundaries
        ↓
Threat modeling
        ↓
Risk assessment
        ↓
Security requirements and control mapping
        ↓
Detections and evidence
        ↓
Incident-response playbooks
        ↓
Isolated laboratory implementation
        ↓
Authorized test cases
```

The project follows a documentation-first approach. Practical components will only be implemented after the logical scope, architecture, assets, flows, and risks have been documented.

## Project Status

### Completed

- mission and assessment scope;
- logical system architecture;
- asset inventory;
- data-flow identification;
- trust-boundary documentation;
- Architecture Overview diagram;
- English and Brazilian Portuguese documentation versions.

### In progress

- threat model;
- risk assessment;
- initial risk register.

### Planned

- security requirements;
- preventive and detective control mapping;
- detection rules;
- incident-response playbooks;
- isolated laboratory implementation;
- authorized test cases;
- synthetic evidence analysis;
- findings, recommendations, and lessons learned.

## Main References

- SPARTA — Space Attack Research and Tactic Analysis;
- NIST IR 8270 — Cybersecurity for Commercial Satellite Operations;
- NIST IR 8401 — Satellite Ground Segment: Applying the Cybersecurity Framework to Satellite Command and Control;
- NIST SP 800-82r3 — Guide to Operational Technology Security;
- NIST SP 800-61r3 — Incident Response Recommendations and Considerations;
- NIST SP 800-30 — Guide for Conducting Risk Assessments;
- CCSDS public standards and recommendations for space data systems;
- additional public references in [references/references.md](./references/references.md).

## Repository Structure

```text
space-ground-segment-assessment/
├── README.md
├── README.pt-BR.md
├── docs/
│   ├── 01-mission-and-scope.md
│   ├── 01-mission-and-scope.pt-BR.md
│   ├── 02-system-architecture.md
│   ├── 02-system-architecture.pt-BR.md
│   ├── 03-asset-inventory.md
│   ├── 03-asset-inventory.pt-BR.md
│   ├── 04-data-flows-and-trust-boundaries-en-US.md
│   ├── 04-data-flows-and-trust-boundaries-pt-BR.md
│   └── architecture/
│       ├── Architecture Overview.drawio
│       ├── Architecture Overview.svg
│       ├── architecture Overview.png
│       └── Architecture Overview-ptbr.jpg
├── diagrams/
├── data/
├── detections/
├── playbooks/
├── lab/
└── references/
```

## About the Author

This independent project is developed by Igor S. Nascimento as part of his Space Cybersecurity learning journey, with a focus on Ground Segment, Mission Operations Center, Blue Team, DFIR, and critical-environment security.

More projects and resources:

- [CEE Orbital](https://l0cu70s.github.io/cee-orbital/);
- [GitHub profile and portfolio](https://github.com/L0CU70S);
- [SPARTA PT-BR Study Guide](https://github.com/L0CU70S/sparta-ptbr-study-guide).

## License

The code, texts, and artifacts in this repository are provided for educational purposes. See [LICENSE](./LICENSE), when available, for the applicable terms.
