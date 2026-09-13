# 1. Mission and Scope

🇺🇸 English | [🇧🇷 Português](01-mission-and-scope.pt-BR.md)

## Mission

AuroraWatch-1 is a fictional Low Earth Orbit (LEO) Earth-observation mission created for cybersecurity learning and portfolio purposes.

The mission is designed to collect fictional environmental imagery and transmit telemetry, mission data, and operational alerts to its Ground Segment.

The scenario focuses on the mission’s terrestrial operational environment, including the Mission Operations Center, operator access, mission-supporting services, ground-station interfaces, and selected third-party dependencies.

## In Scope

The following components, processes, and dependencies are in scope:

- Mission Operations Center (MOC);
- operator workstations;
- mission control servers;
- telemetry processing systems;
- mission data and telemetry storage;
- ground-station gateway;
- identity and access management;
- privileged and remote administrative access;
- security monitoring, logging, and alerting;
- third-party ground-station provider interfaces;
- command and telemetry workflows;
- relevant network connections and trust boundaries between the components above.

## Out of Scope

The following components and activities are outside the scope of this project:

- physical implementation of the satellite;
- spacecraft hardware and embedded-system security testing;
- real radio-frequency (RF) testing or transmission;
- testing or exploitation of real systems;
- access to real satellites, ground stations, mission-control systems, or third-party infrastructure;
- launch vehicle and launch-site security;
- real organization, customer, employee, or operational data;
- real vulnerability disclosure or coordination;
- assessment of regulatory, contractual, safety, or mission-assurance compliance;
- claims about the security posture of any real organization, mission, or provider.

## Assumptions

This assessment is based on the following assumptions:

- AuroraWatch-1 is a fictional Earth-observation mission in Low Earth Orbit;
- the satellite, organizations, users, systems, and providers described in the scenario are fictional;
- operators access mission systems through controlled workstations;
- the Mission Operations Center hosts systems that support command, telemetry, monitoring, and mission operations;
- a fictional third-party provider operates or supports the ground-station interface;
- mission commands and telemetry are exchanged through defined logical interfaces;
- identities, roles, and access privileges can be represented in the laboratory;
- logs can be generated and collected from the simulated systems;
- proposed security controls are design recommendations and have not been independently verified;
- the laboratory will use simulators, synthetic data, and isolated services owned or controlled by the author.

## Assessment Objectives

The project aims to:

- document a simplified Ground Segment architecture;
- identify assets, processes, data flows, and trust boundaries;
- analyze selected space-system threats using public references;
- create an educational risk register;
- propose preventive, detective, and response controls;
- define safe and authorized test cases;
- generate and analyze synthetic security events;
- document findings, limitations, and lessons learned;
- identify opportunities for future improvement and retesting.

## Assessment Approach

The project will follow a progressive, documentation-first approach:

1. Define the mission and scope;
2. model the architecture and trust boundaries;
3. inventory assets and dependencies;
4. document command and telemetry workflows;
5. identify selected threats and risk scenarios;
6. map risks to proposed controls;
7. implement only the required laboratory components;
8. execute authorized tests in the isolated environment;
9. collect and analyze synthetic evidence;
10. document findings, recommendations, and lessons learned.

The project does not claim to be a penetration test, red-team operation, certification, compliance assessment, or complete cybersecurity assessment.

## Limitations

This is a simplified educational assessment and does not represent a real security assessment.

The scenario does not reproduce the full technical, operational, physical, radio-frequency, orbital, software, hardware, safety, regulatory, supply-chain, or mission-assurance complexity of a real space system.

Results will depend on the assumptions, architecture, simulators, synthetic data, test cases, and controls implemented in the laboratory. Findings must not be generalized to real missions, organizations, products, providers, or space systems.

## Responsible Testing Statement

All practical testing associated with this project will be performed only against fictional services, synthetic data, and systems owned or explicitly controlled by the author.

The project will not target real satellites, ground stations, organizations, providers, public infrastructure, production systems, or third-party services.

## Document Status

- Status: Under development
- Scenario: AuroraWatch-1
- Environment: Fictional and isolated laboratory
- Assessment type: Educational portfolio project
- Last reviewed: September 13, 2026
