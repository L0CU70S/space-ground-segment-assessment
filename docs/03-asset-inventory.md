# 3. Asset Inventory

🇺🇸 English | [🇧🇷 Português](03-asset-inventory.pt-BR.md)

## Purpose

This document defines the initial asset inventory for the fictional AuroraWatch-1 Ground Segment.

The inventory supports threat modeling, risk assessment, security-control mapping, monitoring design, incident-response planning, and controlled laboratory testing.

The assets listed here are logical and fictional. They do not represent real systems, products, organizations, providers, or mission infrastructure.

## Inventory Scope

The inventory covers the logical components identified in the AuroraWatch-1 system architecture:

- Operator access;
- identity and privileged access;
- Mission Operations Center;
- command and telemetry services;
- Ground Station Gateway;
- fictional third-party provider interface;
- Satellite Simulator;
- security monitoring;
- cross-cutting services;
- assessment evidence.

The inventory does not represent a complete physical, software, hardware, radio-frequency, orbital, safety, or mission-assurance inventory.

## Inventory Method

Each asset is documented using the following attributes:

- Asset identifier;
- asset name;
- logical segment or zone;
- asset type;
- primary function;
- fictional owner;
- mission or operational role;
- criticality;
- information or process supported;
- dependencies;
- security considerations;
- implementation status;
- planned evidence.

## Criticality Scale

Criticality values are educational classifications for this project:

- **Critical:** compromise or unavailability could directly affect command authority, mission-state integrity, or essential mission operations in the fictional scenario;
- **High:** compromise or unavailability could significantly affect monitoring, processing, access, communications, or investigation;
- **Medium:** compromise or unavailability could affect supporting functions but may not immediately interrupt core mission operations;
- **Low:** compromise or unavailability would have limited impact on the defined scenario.

These classifications are not official risk ratings and must not be applied to real missions without mission-specific impact criteria, risk tolerance, recovery objectives, and stakeholder validation.

## Asset Register

| ID | Asset | Zone | Type | Primary Function | Owner | Criticality | Status |
|---|---|---|---|---|---|---|---|
| A-001 | Operator Workstation | User Access Zone | Endpoint | Access mission applications and review operational information | AuroraWatch Operations | High | Planned |
| A-002 | Identity Provider | Enterprise / Support Zone | Identity Service | Authenticate users and provide identity information | AuroraWatch Security | Critical | Planned |
| A-003 | PAM Service | Administrative Access Zone | Security Service | Control and audit privileged sessions | AuroraWatch Security | Critical | Planned |
| A-004 | Bastion Host | Administrative Access Zone | Administrative System | Provide controlled administrative access | AuroraWatch Infrastructure | High | Planned |
| A-005 | MOC Application | Mission Operations Zone | Application | Support mission monitoring and operational workflows | AuroraWatch Mission Operations | Critical | Planned |
| A-006 | Mission Control Server | Mission Operations Zone | Server / Application | Orchestrate and authorize fictional commands | AuroraWatch Mission Operations | Critical | Planned |
| A-007 | Telemetry Processing System | Mission Operations Zone | Application / Service | Validate, process, and distribute telemetry | AuroraWatch Mission Operations | High | Planned |
| A-008 | Mission Data and Telemetry Storage | Mission Operations Zone | Data Store | Retain mission data, telemetry, and audit records | AuroraWatch Data Services | High | Planned |
| A-009 | Ground Station Gateway | Ground Interface Zone | Gateway / Service | Exchange commands and telemetry with the ground-station interface | AuroraWatch Communications | Critical | Planned |
| A-010 | Third-Party Provider Interface | Ground Interface Zone | External Interface | Represent the fictional provider connection | Fictional GroundLink Provider | High | Planned |
| A-011 | Satellite Simulator | Simulation Zone | Simulator | Represent the fictional space segment | AuroraWatch Mission Engineering | Critical | Planned |
| A-012 | SIEM Platform | Security Monitoring Zone | Security Platform | Collect, correlate, and alert on security events | AuroraWatch Security Operations | High | Planned |
| A-013 | Log Collector | Security Monitoring Zone | Logging Service | Receive and forward logs from laboratory components | AuroraWatch Security Operations | High | Planned |
| A-014 | Configuration Baseline Repository | Cross-Cutting Services | Repository | Store approved configuration baselines and changes | AuroraWatch Infrastructure | Medium | Planned |
| A-015 | Backup and Recovery Storage | Cross-Cutting Services | Storage | Support restoration of selected fictional services and data | AuroraWatch Infrastructure | High | Planned |
| A-016 | Time Synchronization Service | Cross-Cutting Services | Infrastructure Service | Provide consistent timestamps for operations and investigation | AuroraWatch Infrastructure | High | Planned |
| A-017 | Network Security Controls | Cross-Cutting Services | Security Control | Enforce permitted communication paths | AuroraWatch Infrastructure | Critical | Planned |
| A-018 | Assessment Evidence Repository | Security Monitoring Zone | Evidence Repository | Preserve synthetic logs, findings, and test evidence | AuroraWatch Security Operations | High | Planned |

## Detailed Asset Profiles

### A-001 — Operator Workstation

**Purpose:** Provides the operator access point to mission-supporting applications.

**Supported processes:**

- user authentication;
- telemetry review;
- command request and approval;
- alert review;
- operational documentation;
- security-event generation.

**Information handled:** credentials, session data, telemetry views, command requests, operational alerts, and local security logs.

**Dependencies:** Identity Provider, MOC Application, network security controls, time synchronization, and SIEM or Log Collector.

**Security considerations:** endpoint compromise, credential theft, unauthorized software, excessive local privilege, unapproved remote access, malware execution, and incomplete endpoint logging.

**Planned evidence:** endpoint configuration baseline, authentication events, process events, network events, and approved user-access record.

### A-002 — Identity Provider

**Purpose:** Authenticates users and supplies identity and role information.

**Supported processes:**

- account lifecycle;
- authentication;
- authorization;
- access review;
- identity monitoring.

**Information handled:** identities, authentication events, roles, group membership, and access decisions.

**Dependencies:** directory or identity database, time synchronization, network security controls, and SIEM.

**Security considerations:** privileged identity compromise, weak authentication, excessive roles, account persistence, insecure recovery processes, and log tampering.

**Planned evidence:** successful and failed authentication logs, role assignments, account-review record, and access-policy configuration.

### A-003 — PAM Service

**Purpose:** Controls access to privileged accounts and administrative sessions.

**Supported processes:**

- privileged-access approval;
- session brokering;
- credential protection;
- session recording;
- access review.

**Information handled:** privileged identities, access requests, session metadata, approvals, and audit records.

**Dependencies:** Identity Provider, Bastion Host, Mission Operations systems, SIEM, and time synchronization.

**Security considerations:** bypassed access path, shared accounts, incomplete session records, excessive standing privilege, and unauthorized credential retrieval.

**Planned evidence:** privileged-access request, session record, approval trail, and access-review output.

### A-004 — Bastion Host

**Purpose:** Provides a controlled path for administrative access to mission-supporting systems.

**Supported processes:**

- secure administration;
- session logging;
- access restriction;
- administrative investigation.

**Information handled:** administrative sessions, commands, authentication events, and system logs.

**Dependencies:** PAM Service, Identity Provider, network security controls, SIEM, and time synchronization.

**Security considerations:** direct-access bypass, host compromise, weak SSH configuration, excessive administrative commands, and insufficient session logging.

**Planned evidence:** access-control rules, authentication logs, session records, configuration baseline, and administrative command history.

### A-005 — MOC Application

**Purpose:** Provides the operational interface for mission monitoring and workflow management.

**Supported processes:**

- telemetry display;
- command workflow;
- alert handling;
- operator coordination;
- audit generation.

**Information handled:** mission status, telemetry views, command requests, approvals, alerts, and audit events.

**Dependencies:** Identity Provider, Mission Control Server, Telemetry Processing System, storage, Ground Station Gateway, and SIEM.

**Security considerations:** unauthorized command requests, broken authorization, application compromise, injection into operational data, and incomplete audit trails.

**Planned evidence:** application logs, access decisions, command workflow records, and audit events.

### A-006 — Mission Control Server

**Purpose:** Orchestrates the fictional command workflow and maintains mission state.

**Supported processes:**

- command validation;
- approval enforcement;
- command forwarding;
- acknowledgement processing;
- audit logging.

**Information handled:** command requests, command approvals, mission state, acknowledgements, and administrative events.

**Dependencies:** MOC Application, Ground Station Gateway, Identity Provider, storage, time synchronization, and SIEM.

**Security considerations:** unauthorized command execution, command replay, privilege escalation, state manipulation, service compromise, and insufficient separation of duties.

**Planned evidence:** command audit record, authorization result, sequence validation, state transition record, and service logs.

### A-007 — Telemetry Processing System

**Purpose:** Validates, normalizes, and distributes simulated telemetry.

**Supported processes:**

- message reception;
- source and format validation;
- anomaly detection;
- normalization;
- display;
- storage.

**Information handled:** telemetry messages, validation results, anomaly records, processing status, and timestamps.

**Dependencies:** Ground Station Gateway, MOC Application, storage, time synchronization, and SIEM.

**Security considerations:** malformed input, false telemetry, message replay, data manipulation, denial of service, and insufficient source validation.

**Planned evidence:** telemetry records, validation events, anomaly alerts, source metadata, and processing logs.

### A-008 — Mission Data and Telemetry Storage

**Purpose:** Retains fictional mission data, telemetry, audit events, and selected evidence.

**Supported processes:**

- data retention;
- retrieval;
- investigation;
- reporting;
- recovery.

**Information handled:** mission data, telemetry, command records, audit records, and operational history.

**Dependencies:** MOC Application, Mission Control Server, Telemetry Processing System, Backup and Recovery Storage, access management, and SIEM.

**Security considerations:** unauthorized modification, deletion, data exposure, weak retention, backup compromise, and inadequate integrity protection.

**Planned evidence:** access logs, integrity checks, backup record, retention configuration, and recovery test output.

### A-009 — Ground Station Gateway

**Purpose:** Enforces the logical exchange between mission operations and the fictional ground-station interface.

**Supported processes:**

- command forwarding;
- telemetry reception;
- message validation;
- rate control;
- transaction logging.

**Information handled:** command messages, telemetry messages, interface metadata, authorization data, sequence numbers, and timestamps.

**Dependencies:** Mission Control Server, Telemetry Processing System, Third-Party Provider Interface, network security controls, time synchronization, and SIEM.

**Security considerations:** unauthorized forwarding, replay, message manipulation, exposed service interfaces, provider access abuse, and service disruption.

**Planned evidence:** gateway transaction log, message-validation result, connection record, rate-limit event, and configuration baseline.

### A-010 — Third-Party Provider Interface

**Purpose:** Represents the external logical dependency used to exchange commands and telemetry.

**Supported processes:**

- provider access;
- service exchange;
- operational coordination;
- provider event reporting.

**Information handled:** interface messages, service metadata, access records, and provider security events.

**Dependencies:** Ground Station Gateway, contractual assumptions, identity and access controls, and network security controls.

**Security considerations:** unclear responsibility boundaries, excessive access, weak provider authentication, insufficient logging, supply-chain risk, and service dependency risk.

**Planned evidence:** provider access list, security requirements, service-level assumptions, connection logs, and review record.

### A-011 — Satellite Simulator

**Purpose:** Represents the fictional space segment without connecting to a real spacecraft or radio system.

**Supported processes:**

- command acceptance;
- simulated state transitions;
- telemetry generation;
- acknowledgements;
- simulated anomalies.

**Information handled:** fictional commands, simulated state, telemetry, sequence numbers, timestamps, and test results.

**Dependencies:** Ground Station Gateway, simulation data, time synchronization, and logging.

**Security considerations:** invalid state transitions, insufficient command validation, replay, telemetry-integrity failure, test escape, and unsafe simulator behavior.

**Planned evidence:** simulator state record, accepted/rejected commands, telemetry output, anomaly record, and test log.

### A-012 — SIEM Platform

**Purpose:** Centralizes and analyzes security-relevant events.

**Supported processes:**

- log collection;
- correlation;
- alerting;
- investigation;
- reporting;
- evidence support.

**Information handled:** authentication events, endpoint events, command events, telemetry events, configuration changes, alerts, and investigation data.

**Dependencies:** Log Collector, time synchronization, storage, detection rules, and analyst access.

**Security considerations:** missing log sources, incorrect parsing, alert fatigue, unauthorized access, retention failure, and log manipulation.

**Planned evidence:** ingestion status, detection rule, alert record, analyst notes, and case timeline.

### A-013 — Log Collector

**Purpose:** Receives and forwards logs from laboratory components.

**Supported processes:**

- log transport;
- buffering;
- normalization;
- forwarding;
- health monitoring.

**Information handled:** security logs, operational logs, metadata, timestamps, and collection status.

**Dependencies:** network security controls, SIEM, time synchronization, and source systems.

**Security considerations:** log loss, unauthorized injection, insecure transport, queue exhaustion, and insufficient availability.

**Planned evidence:** source inventory, collection configuration, delivery status, dropped-event record, and health check.

### A-014 — Configuration Baseline Repository

**Purpose:** Stores approved configurations, baselines, changes, and comparison data.

**Supported processes:**

- change management;
- baseline comparison;
- integrity monitoring;
- rollback support.

**Information handled:** configuration files, hashes, approval records, version history, and change metadata.

**Dependencies:** access management, storage, version control, and SIEM.

**Security considerations:** unauthorized changes, baseline tampering, lack of approval records, and inability to determine the expected state.

**Planned evidence:** approved baseline, change request, version history, integrity comparison, and rollback record.

### A-015 — Backup and Recovery Storage

**Purpose:** Supports recovery of selected fictional services and data.

**Supported processes:**

- backup;
- restoration;
- recovery testing;
- continuity exercises.

**Information handled:** system backups, configuration backups, data snapshots, and recovery metadata.

**Dependencies:** storage, access management, scheduling, and network security controls.

**Security considerations:** untested restoration, backup deletion, exposed backup data, insufficient separation, and outdated recovery points.

**Planned evidence:** backup job record, restore test, access log, retention policy, and recovery result.

### A-016 — Time Synchronization Service

**Purpose:** Provides consistent timestamps across laboratory components.

**Supported processes:**

- event correlation;
- command validity;
- log analysis;
- incident timelines.

**Information handled:** time-source metadata, synchronization status, offset measurements, and system timestamps.

**Dependencies:** host time source, network security controls, and system configuration.

**Security considerations:** clock drift, malicious time changes, inconsistent timestamps, and unreliable investigation timelines.

**Planned evidence:** synchronization status, offset record, time-source configuration, and drift alert.

### A-017 — Network Security Controls

**Purpose:** Enforces communication paths between logical zones and services.

**Supported processes:**

- segmentation;
- filtering;
- access restriction;
- monitoring;
- containment.

**Information handled:** network flows, rule sets, connection attempts, blocked traffic, and configuration changes.

**Dependencies:** network topology, approved flows, firewall or host controls, logging, and time synchronization.

**Security considerations:** overly permissive rules, direct access paths, unmonitored traffic, rule drift, and inadequate isolation.

**Planned evidence:** approved rule set, blocked connection event, change record, flow log, and review result.

### A-018 — Assessment Evidence Repository

**Purpose:** Preserves synthetic logs, findings, screenshots, test records, and analysis notes.

**Supported processes:**

- evidence handling;
- reproducibility;
- reporting;
- review;
- lessons learned.

**Information handled:** synthetic evidence, investigation notes, screenshots, test outputs, reports, and timestamps.

**Dependencies:** access management, storage, integrity controls, backup, and time synchronization.

**Security considerations:** evidence alteration, accidental exposure, unclear provenance, missing timestamps, and inadequate retention.

**Planned evidence:** evidence index, hash or integrity record, access history, chain-of-custody note, and final report.

## Asset Relationships

### Operational command path

```text
A-001 Operator Workstation
        ↓
A-005 MOC Application
        ↓
A-006 Mission Control Server
        ↓
A-009 Ground Station Gateway
        ↓
A-011 Satellite Simulator
```

### Telemetry path

```text
A-011 Satellite Simulator
        ↓
A-009 Ground Station Gateway
        ↓
A-007 Telemetry Processing System
        ↓
A-005 MOC Application
        ↓
A-008 Mission Data and Telemetry Storage
```

### Authentication and privileged-access path

```text
A-001 Operator Workstation
        ↓
A-002 Identity Provider
        ↓
A-005 MOC Application
```

```text
A-001 Operator Workstation
        ↓
A-003 PAM Service
        ↓
A-004 Bastion Host
        ↓
Mission Operations systems
```

### Security-monitoring path

```text
Relevant laboratory components
        ↓
A-013 Log Collector
        ↓
A-012 SIEM Platform
        ↓
A-018 Assessment Evidence Repository
```

## Cross-Cutting Services

The following assets support multiple logical zones:

- A-014 Configuration Baseline Repository;
- A-015 Backup and Recovery Storage;
- A-016 Time Synchronization Service;
- A-017 Network Security Controls.

These assets should not be interpreted as belonging exclusively to one operational zone. Their security posture can affect multiple components simultaneously.

## Initial Criticality Considerations

The following assets are initially considered critical because they influence command authority, mission-state integrity, communications, or access control:

- A-002 Identity Provider;
- A-003 PAM Service;
- A-005 MOC Application;
- A-006 Mission Control Server;
- A-009 Ground Station Gateway;
- A-011 Satellite Simulator;
- A-017 Network Security Controls.

This is an initial educational classification. The final risk of an asset will depend on mission impact, threat exposure, existing controls, dependencies, recovery objectives, and risk tolerance.

## Initial Security Properties

The project will evaluate the following security properties for relevant assets:

| Property | Example in AuroraWatch-1 |
|---|---|
| Confidentiality | Protect credentials, mission data, and security evidence |
| Integrity | Prevent unauthorized changes to commands, telemetry, configurations, and logs |
| Availability | Maintain access to MOC, telemetry, command workflows, and monitoring |
| Authenticity | Verify operators, services, commands, telemetry sources, and provider interfaces |
| Accountability | Record actions, approvals, changes, and security events |
| Recoverability | Restore selected systems, configurations, and data after disruption |
| Safety and mission assurance | Avoid unsafe simulated state transitions and uncontrolled test behavior |

## Inventory Limitations

This inventory is not exhaustive. It currently focuses on logical assets necessary to explain the first assessment phase.

Future versions may add:

- software and service identifiers;
- data classifications;
- interfaces and ports;
- authentication methods;
- backup objectives;
- recovery-time and recovery-point objectives;
- asset owners and custodians;
- security-control references;
- monitoring coverage;
- vulnerability and configuration status;
- physical and environmental dependencies;
- cryptographic dependencies and key-management roles;
- supplier responsibilities and contractual controls.

## Document Status

- Status: Under development
- Scenario: AuroraWatch-1
- Environment: Fictional and isolated laboratory
- Assessment type: Educational portfolio project
- Language: English
- Last reviewed: September 18, 2026
