# AuroraWatch-1 Ground Segment Cybersecurity Assessment

🇺🇸 English | [🇧🇷 Português](README.pt-BR.md)

Fictional educational cybersecurity assessment of the Ground Segment and Mission Operations Center of a simulated space mission.

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

## Initial Scope

The initial scope includes:

- Operator workstations;
- Mission Operations Center systems;
- telemetry processing;
- telecommand workflows;
- ground-station gateway;
- identity, authentication, and privileged access;
- security monitoring and logging;
- dependencies on a fictional ground-station provider;
- satellite simulator.

Detailed scope information is documented in [`docs/01-mission-and-scope.md`](docs/01-mission-and-scope.md).

## Study Methodology

The assessment will be developed progressively:

1. Define the mission and assessment scope;
2. model the system architecture;
3. create an asset inventory;
4. identify data flows and trust boundaries;
5. select relevant threats;
6. create and prioritize a risk register;
7. map preventive and detective controls;
8. create authorized test cases;
9. analyze logs and evidence;
10. document response procedures and lessons learned.

When implemented, practical tests will be conducted only in an isolated, controlled environment owned by the author, using simulators and fictional services.

## Main References

- SPARTA — Space Attack Research and Tactic Analysis;
- NIST IR 8270 — Cybersecurity for Commercial Satellite Operations;
- NIST IR 8401 — Satellite Ground Segment: Applying the Cybersecurity Framework to Satellite Command and Control;
- NIST SP 800-82r3 — Guide to Operational Technology (OT) Security;
- NIST SP 800-61r3 — Incident Response Recommendations and Considerations;
- NIST SP 800-30 — Guide for Conducting Risk Assessments;
- CCSDS — public standards and recommendations for space data systems;
- additional public references identified in [`references/references.md`](references/references.md).

## Project Structure

```text
space-ground-segment-assessment/
├── README.md
├── README.pt-BR.md
├── docs/
│   ├── 01-mission-and-scope.md
│   └── 02-system-architecture.md
├── diagrams/
├── data/
├── detections/
├── playbooks/
├── lab/
└── references/
```

The structure will be expanded as new artifacts are developed.

## Status

🚧 In development.

The first stage of the project consists of defining the mission, scope, and architecture of the fictional scenario before implementing simulators and test cases.

## About the Author

This is an independent project developed by Igor S. Nascimento as part of his Space Cybersecurity learning journey, with a focus on Ground Segment, Mission Operations Center, Blue Team, DFIR, and critical-environment security.

More projects and resources:

- [CEE Orbital](https://l0cu70s.github.io/cee-orbital/)
- [GitHub profile and portfolio](https://github.com/L0CU70S)
- [SPARTA PT-BR Study Guide](https://github.com/L0CU70S/sparta-ptbr-study-guide)

## License

The code, texts, and artifacts in this repository are provided for educational purposes. See [`LICENSE`](LICENSE), when available, for the applicable terms.

> Learn, model, test responsibly, document, and share.
