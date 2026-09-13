# 2. System Architecture

🇺🇸 English | [🇧🇷 Português](02-system-architecture.pt-BR.md)

## Purpose

This document describes the logical architecture of the fictional AuroraWatch-1 Ground Segment used in this educational assessment.

The architecture is intentionally simplified. It is designed to support asset identification, data-flow analysis, trust-boundary definition, threat modeling, risk assessment, security monitoring, and controlled laboratory testing.

It does not reproduce the architecture of a real satellite mission, organization, provider, or operational environment.

## Mission Context

AuroraWatch-1 is a fictional Low Earth Orbit (LEO) Earth-observation mission.

The mission collects fictional environmental imagery and operational telemetry. Mission operators use the Ground Segment to monitor mission status, process telemetry, prepare commands, exchange data with a fictional ground-station provider, and record operational events.

The satellite and radio-frequency layer are represented by a simulator. No real spacecraft, antenna, radio transmission, or operational mission-control system is connected to this project.

## Logical Components

### 1. Operator Workstation

The Operator Workstation is used by authorized mission operators to access mission-supporting applications.

Expected functions:

- access the MOC application;
- review telemetry and mission status;
- submit or approve fictional command requests;
- review operational alerts;
- access approved documentation;
- generate workstation and authentication logs.

Security considerations:

- individual user accounts;
- least privilege;
- endpoint hardening;
- multi-factor authentication where supported;
- session and activity logging;
- restricted administrative access.

### 2. Identity Provider

The Identity Provider manages authentication and identity-related services for the laboratory.

Expected functions:

- authenticate users;
- provide role information;
- support access reviews;
- record successful and failed authentication events;
- provide identity data to the MOC and privileged-access workflows.

Security considerations:

- strong authentication;
- account lifecycle management;
- role-based access control;
- privileged-account protection;
- authentication-event monitoring;
- secure time synchronization.

### 3. Privileged Access Management

The fictional PAM component controls privileged access to sensitive mission-supporting systems.

Expected functions:

- broker administrative sessions;
- restrict access to approved users;
- record session metadata;
- support time-limited or task-based access;
- provide audit information to the monitoring platform.

The PAM component may be implemented as a documented control or as a laboratory service, depending on the project phase.

### 4. Bastion Host

The Bastion Host is the controlled administrative access point for mission-supporting servers.

Expected functions:

- provide a controlled path for administration;
- limit direct administrative access to protected systems;
- generate authentication and session logs;
- support administrative access reviews.

Security considerations:

- restricted network access;
- individual accounts;
- SSH keys or equivalent secure authentication;
- limited administrative commands;
- session logging;
- centralized log forwarding;
- hardened configuration.

### 5. Mission Operations Center

The Mission Operations Center is the central logical environment for mission operations.

Expected functions:

- display mission status;
- receive and process telemetry;
- prepare and authorize fictional commands;
- manage operational workflows;
- generate mission and audit events;
- communicate with the Ground Station Gateway.

The MOC may include several logical services even when they are implemented on a single laboratory host.

### 6. Mission Control Server

The Mission Control Server supports command orchestration and mission-state management.

Expected functions:

- receive approved command requests;
- validate command structure and authorization;
- apply command workflow rules;
- transmit accepted commands to the Ground Station Gateway;
- record command and administrative events.

Security considerations:

- strong authentication;
- command authorization;
- separation of duties;
- command allowlisting;
- replay protection in the simulator;
- complete audit logging;
- restricted network exposure.

### 7. Telemetry Processing System

The Telemetry Processing System receives and processes simulated telemetry.

Expected functions:

- receive telemetry messages;
- validate message format and source;
- normalize telemetry data;
- identify abnormal or missing data;
- provide data to the MOC;
- record processing and validation events.

Security considerations:

- input validation;
- source authentication;
- integrity monitoring;
- anomaly detection;
- service-account restrictions;
- centralized logging.

### 8. Mission Data and Telemetry Storage

The storage component retains fictional mission data, telemetry, audit events, and assessment evidence.

Expected functions:

- store telemetry;
- store mission-event records;
- preserve audit logs;
- support investigation and analysis;
- provide controlled access to authorized services.

Security considerations:

- access control;
- data integrity;
- backup and recovery;
- retention rules;
- protection against unauthorized deletion or modification;
- separation of operational data and security evidence.

### 9. Ground Station Gateway

The Ground Station Gateway represents the logical interface between the Mission Operations Center and the fictional third-party ground-station provider.

Expected functions:

- receive approved commands from the MOC;
- validate message structure and authorization data;
- forward fictional commands to the Satellite Simulator;
- receive simulated telemetry;
- forward telemetry to the Telemetry Processing System;
- record all transactions.

Security considerations:

- explicit allowlists;
- authenticated service-to-service communication;
- command validation;
- sequence and timestamp validation;
- rate limiting;
- complete transaction logging;
- strict network boundaries.

### 10. Third-Party Ground Station Provider

The Third-Party Ground Station Provider is a fictional external dependency that supports the ground-station interface.

Expected functions:

- provide a logical station interface;
- receive authorized fictional commands;
- transmit simulated telemetry;
- provide service and security events;
- support operational coordination.

Security considerations:

- contractual and access boundaries;
- least privilege;
- individual identities;
- time-limited access;
- provider logging;
- change management;
- incident-notification procedures.

No real provider, external account, external network, or real ground station is used.

### 11. Satellite Simulator

The Satellite Simulator represents the space segment in the laboratory.

Expected functions:

- accept only fictional and validated commands;
- update simulated mission state;
- generate fictional telemetry;
- return command acknowledgements;
- generate simulated anomalies;
- record state changes and command results.

The simulator does not model the complete hardware, software, orbital, radio-frequency, safety, or operational complexity of a real spacecraft.

### 12. Security Monitoring and SIEM

The Security Monitoring and SIEM component collects and analyzes security-relevant events from the laboratory.

Expected functions:

- collect authentication logs;
- collect privileged-access events;
- collect MOC and gateway audit records;
- detect suspicious or unauthorized activity;
- support alert triage;
- preserve investigation evidence;
- support incident-response exercises.

Potential log sources:

- operator workstation;
- Identity Provider;
- PAM and Bastion Host;
- Mission Control Server;
- Telemetry Processing System;
- Ground Station Gateway;
- Satellite Simulator;
- network controls;
- configuration-monitoring tools.

## Logical Network Zones

The laboratory is organized into logical security zones. These zones are conceptual and may be implemented using virtual networks, containers, host-based controls, or documented boundaries depending on the project phase.

### User Access Zone

Contains operator workstations and user-facing access paths.

Primary concerns:

- endpoint compromise;
- credential theft;
- unauthorized access;
- excessive privileges;
- malicious or accidental operator activity.

### Enterprise or Support Zone

Represents supporting identity, administration, and shared services.

Primary concerns:

- lateral movement;
- identity compromise;
- excessive administrative access;
- insecure dependencies.

### Administrative Access Zone

Contains the Bastion Host and privileged-access workflows.

Primary concerns:

- privileged-account compromise;
- session abuse;
- direct access to protected systems;
- inadequate audit trails.

### Mission Operations Zone

Contains the MOC, Mission Control Server, Telemetry Processing System, and mission data services.

Primary concerns:

- unauthorized commands;
- manipulation of mission data;
- loss of availability;
- insufficient separation of duties;
- incomplete logging.

### Ground Interface Zone

Contains the Ground Station Gateway and its logical interface with the fictional provider.

Primary concerns:

- unauthorized command forwarding;
- message manipulation;
- replay;
- provider access;
- service disruption.

### Simulation Zone

Contains the Satellite Simulator and controlled test services.

Primary concerns:

- invalid state transitions;
- command-validation weaknesses;
- telemetry integrity;
- test isolation.

### Security Monitoring Zone

Contains log collection, analysis, alerting, and evidence-preservation services.

Primary concerns:

- log loss;
- log manipulation;
- insufficient time synchronization;
- excessive access to security evidence;
- incomplete visibility.

## Primary Data Flows

### Flow F-01 — Operator Authentication

```text
Operator Workstation
        ↓
Identity Provider
        ↓
MOC Application
```

Purpose:

- authenticate the operator;
- obtain role and authorization information;
- record authentication and access events.

### Flow F-02 — Privileged Administrative Access

```text
Operator Workstation
        ↓
Bastion Host / PAM
        ↓
Mission Operations Systems
```

Purpose:

- provide controlled administrative access;
- limit direct connections;
- record privileged activity.

### Flow F-03 — Mission Command

```text
Operator Workstation
        ↓
MOC Application
        ↓
Mission Control Server
        ↓
Ground Station Gateway
        ↓
Satellite Simulator
```

Purpose:

- submit a fictional command;
- validate authorization and structure;
- forward an approved command;
- receive a simulated acknowledgement;
- record the complete workflow.

### Flow F-04 — Telemetry

```text
Satellite Simulator
        ↓
Ground Station Gateway
        ↓
Telemetry Processing System
        ↓
MOC Application
        ↓
Mission Data and Telemetry Storage
```

Purpose:

- transmit simulated telemetry;
- validate and process telemetry;
- display mission information;
- retain data for operations and investigation.

### Flow F-05 — Security Logging

```text
Laboratory Components
        ↓
Log Collectors
        ↓
Security Monitoring / SIEM
        ↓
Alerts and Investigation Evidence
```

Purpose:

- centralize security-relevant events;
- detect abnormal activity;
- support investigation and response;
- preserve evidence.

## Trust Boundaries

The following trust boundaries require explicit documentation and security controls:

- between the operator workstation and the MOC;
- between the user-access zone and the administrative-access zone;
- between the Bastion Host and mission-supporting systems;
- between the MOC and the Ground Station Gateway;
- between the Ground Station Gateway and the fictional provider interface;
- between the Ground Station Gateway and the Satellite Simulator;
- between operational systems and the SIEM;
- between mission data and security evidence;
- between laboratory services and the host environment.

## Initial Security Principles

The architecture will be evaluated using the following principles:

- least privilege;
- deny by default;
- explicit authorization;
- separation of duties;
- defense in depth;
- secure administration paths;
- segmentation and controlled communication;
- authenticated and integrity-protected data flows;
- complete and centralized logging;
- time synchronization;
- controlled change management;
- recovery and evidence preservation;
- safe testing in an isolated environment.

## Architecture Limitations

This logical architecture is an initial design for an educational laboratory. It does not define:

- a real spacecraft architecture;
- a real radio-frequency link;
- a real cryptographic design;
- a real mission-control protocol;
- a real provider integration;
- a complete safety or mission-assurance architecture;
- a production-ready deployment.

Specific technologies, network addresses, protocols, containers, virtual machines, and security controls will be documented only when they are implemented in the controlled laboratory.

## Next Steps

The next architecture activities are:

- [x] 1. create a visual architecture diagram; 
- [ ] 2. assign identifiers to components and trust boundaries;
- [ ] 3. create the asset inventory;
- [ ] 4. document data-flow assumptions;
- [ ] 5. define initial security requirements;
- [ ] 6. select the first controlled test cases;
- [ ] 7. map relevant threats and risks to the architecture.

## Document Status

- Status: Under development
- Scenario: AuroraWatch-1
- Environment: Fictional and isolated laboratory
- Assessment type: Educational portfolio project
- Last reviewed: September 13, 2026
