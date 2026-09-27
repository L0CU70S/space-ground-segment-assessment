# AuroraWatch-1
## Data Flows and Trust Boundaries

**Document ID:** DOC-04  
**Version:** 0.1  
**Status:** In Development  
**Scenario:** Fictional educational scenario  
**Related documents:** DOC-01 Mission and Scope; DOC-02 System Architecture; DOC-03 Asset Inventory

**Language:** [Português do Brasil](./04-data-flows-and-trust-boundaries-pt-BR.md)

> This document describes a fictional educational architecture. It does not represent a real spacecraft, mission, organization, or production system.

---

## Architecture Overview

The logical architecture described in this document is available in the repository:

- [Architecture Overview — PNG](./architecture/architecture%20Overview.png)
- [Architecture Overview — SVG](./architecture/Architecture%20Overview.svg)
- [Architecture Overview — JPG, Brazilian Portuguese](./architecture/Architecture%20Overview-ptbr.jpg)
- [Editable draw.io source](./architecture/Architecture%20Overview.drawio)

> The JPG image is the Brazilian Portuguese version of the architecture. The structure and asset identifiers are the same in both language versions.

---

## 1. Purpose and Scope

This document identifies and describes the logical communication flows and trust boundaries represented in the AuroraWatch-1 Ground Segment Architecture Overview.

It provides traceability between the visual architecture and the formal assessment documentation. Flow identifiers such as F-01 and F-02 are documentation identifiers. They are not required to appear as numbers on the diagram.

The document covers:

- authentication and authorization flows;
- privileged-administration flows;
- mission-operation and command flows;
- telecommand uplink and telemetry downlink;
- telemetry processing and mission-data flows;
- third-party interface flows;
- security-event collection and monitoring;
- cross-cutting services;
- logical trust boundaries.

The flows are logical representations. They do not define real IP addresses, ports, protocols, cryptographic algorithms, keys, network routes, or operational procedures.

## 2. Flow-Identification Convention

Each documented connection uses the following format:

```text
F-XX — Flow name
Source → Destination
Purpose
Security considerations
```

The diagram uses colors and line styles to communicate the category of each flow. This document adds formal identifiers and descriptions so that later threat modeling and control mapping can refer to a specific connection.

A single logical flow may represent multiple technical connections in a real implementation. Conversely, a single technical connection may carry multiple logical data types. This document intentionally remains at the logical-architecture level.

## 3. Flow Legend

| Diagram style | Meaning |
|---|---|
| Gray dotted | Authentication and authorization |
| Yellow dashed | Privileged administration |
| Cyan solid | Mission operations |
| Orange solid | Telecommand uplink |
| Red solid | Telemetry downlink and telemetry ingestion |
| Pink dotted | Mission data and processed telemetry |
| Green dotted | Security events from monitored assets |
| Green solid | Centralized log ingestion and evidence handling |
| Wine dashed | External provider interface |
| Gold dashed | Cross-cutting services and policy enforcement |

The colored containers represent logical zones. They are not themselves data flows.

## 4. Flow Inventory

| ID | Source | Destination | Diagram label | Category |
|---|---|---|---|---|
| F-01 | A-001 | A-002 | User Authentication | Authentication |
| F-02 | A-002 | A-003 | Privileged Access Authorization | Authorization |
| F-03 | A-003 | A-004 | Privileged Session | Privileged administration |
| F-04 | A-004 | A-005 | Administrative Access | Privileged administration |
| F-05 | A-005 | A-006 | Mission Operations Commands | Mission operations |
| F-06 | A-006 | A-009 | Command Uplink Path | Mission operations |
| F-07 | A-009 | A-011 | Telecommand Uplink | TT&C |
| F-08 | A-011 | A-009 | Telemetry Downlink | TT&C |
| F-09 | A-009 | A-007 | Telemetry Ingestion | Telemetry processing |
| F-10 | A-007 | A-005 | Processed Telemetry | Mission data |
| F-11 | A-007 | A-008 | Mission Data Storage | Mission data |
| F-12 | A-008 | A-005 | Mission Data Retrieval | Mission data |
| F-13 | A-009 | A-010 | External Provider Interface | External dependency |
| F-14 | A-010 | A-009 | External Provider Response | External dependency |
| F-15 | Monitored assets | A-013 | Security Event Collection | Logging |
| F-16 | A-013 | A-012 | Centralized Log Ingestion | Monitoring |
| F-17 | A-012 | A-018 | Security Evidence Retention | Evidence |
| F-18 | A-014 | Authorized assets | Configuration Baseline | Cross-cutting service |
| F-19 | Authorized assets | A-015 | Backup and Recovery | Cross-cutting service |
| F-20 | A-016 | Mission and security assets | Time Synchronization | Cross-cutting service |
| F-21 | A-017 | Zone boundaries | Policy Enforcement | Cross-cutting control |

## 5. Authentication and Administration Flows

### F-01 — User Authentication

**Source:** A-001 Operator Workstation  
**Destination:** A-002 Identity Provider  
**Diagram style:** Gray dotted  
**Purpose:** Authenticate the operator before access is granted to protected services.  
**Security considerations:** Authentication assurance, MFA, credential protection, endpoint trust, confidentiality, integrity, availability, and accountability.  
**Events:** Successful and failed authentication, MFA results, lockouts, account changes, and policy changes.

### F-02 — Privileged Access Authorization

**Source:** A-002 Identity Provider  
**Destination:** A-003 PAM Service  
**Diagram style:** Gray dotted  
**Purpose:** Provide identity and authorization information for a privileged-access decision.  
**Security considerations:** Role and attribute evaluation, least privilege, approval requirements, separation of duties, and authorization integrity.

### F-03 — Privileged Session

**Source:** A-003 PAM Service  
**Destination:** A-004 Bastion Host  
**Diagram style:** Yellow dashed  
**Purpose:** Establish and control an approved administrative session through the bastion host.  
**Security considerations:** Session authorization, credential protection, session isolation, command accountability, and termination.

### F-04 — Administrative Access

**Source:** A-004 Bastion Host  
**Destination:** A-005 MOC Application and, where explicitly authorized, A-006 Mission Control Server  
**Diagram style:** Yellow dashed  
**Purpose:** Provide controlled administrative access to mission systems.  
**Security considerations:** Bastion enforcement, least privilege, MFA, administrative authorization, session accountability, and network policy enforcement.

> The administrative path is distinct from the mission-command path. A-004 is not part of the normal operational command flow.

## 6. Mission Operations and Command Flows

### F-05 — Mission Operations Commands

**Source:** A-005 MOC Application  
**Destination:** A-006 Mission Control Server  
**Diagram style:** Cyan solid  
**Purpose:** Submit and coordinate authorized mission-operation commands.  
**Security considerations:** Authentication, authorization, command integrity, availability, accountability, validation, and separation of duties.

### F-06 — Command Uplink Path

**Source:** A-006 Mission Control Server  
**Destination:** A-009 Ground Station Gateway  
**Diagram style:** Cyan solid  
**Purpose:** Deliver approved mission commands to the ground interface.  
**Security considerations:** Command integrity, source authentication, authorization, availability, input validation, and gateway policy enforcement.

### F-07 — Telecommand Uplink

**Source:** A-009 Ground Station Gateway  
**Destination:** A-011 Satellite Simulator  
**Diagram style:** Orange solid  
**Purpose:** Transmit telecommands to the simulated space-segment endpoint.  
**Security considerations:** Authentication, integrity, authorization, availability, anti-replay protection, protocol validation, and test-environment isolation.

> This is a fictional logical model. It does not define a real CCSDS implementation, cryptographic profile, or flight-qualified command path.

## 7. Telemetry and Mission-Data Flows

### F-08 — Telemetry Downlink

**Source:** A-011 Satellite Simulator  
**Destination:** A-009 Ground Station Gateway  
**Diagram style:** Red solid  
**Purpose:** Return simulated telemetry and status data to the ground interface.  
**Security considerations:** Integrity, source authenticity where required, confidentiality where required, availability, input validation, and accountability.

### F-09 — Telemetry Ingestion

**Source:** A-009 Ground Station Gateway  
**Destination:** A-007 Telemetry Processing System  
**Diagram style:** Red solid  
**Purpose:** Transfer received telemetry for decoding, validation, and processing.  
**Security considerations:** Integrity, availability, input validation, resource protection, and accountability.

### F-10 — Processed Telemetry

**Source:** A-007 Telemetry Processing System  
**Destination:** A-005 MOC Application  
**Diagram style:** Pink dotted  
**Purpose:** Present processed telemetry and mission status to authorized operators.  
**Security considerations:** Integrity, availability, authorization, confidentiality where applicable, and accountability.

### F-11 — Mission Data Storage

**Source:** A-007 Telemetry Processing System  
**Destination:** A-008 Mission Data and Telemetry Storage  
**Diagram style:** Pink dotted  
**Purpose:** Store processed telemetry, mission data, and related operational records.  
**Security considerations:** Confidentiality, integrity, availability, access control, retention, and accountability.

### F-12 — Mission Data Retrieval

**Source:** A-008 Mission Data and Telemetry Storage  
**Destination:** A-005 MOC Application  
**Diagram style:** Pink dotted  
**Purpose:** Provide authorized access to stored mission data and historical telemetry.  
**Security considerations:** Confidentiality, integrity, authorization, export control, and accountability.

## 8. External-Provider Flows

### F-13 — External Provider Interface

**Source:** A-009 Ground Station Gateway  
**Destination:** A-010 Third-Party Provider Interface  
**Diagram style:** Wine dashed  
**Purpose:** Exchange approved service requests or operational data with a third-party provider.  
**Security considerations:** Mutual authentication, authorization, least privilege, interface validation, confidentiality where required, integrity, provider risk, and accountability.

### F-14 — External Provider Response

**Source:** A-010 Third-Party Provider Interface  
**Destination:** A-009 Ground Station Gateway  
**Diagram style:** Wine dashed  
**Purpose:** Return approved service responses or data to the gateway.  
**Security considerations:** Source authentication, integrity, input validation, availability, and accountability.

> The external provider interface is not part of the direct telecommand path unless a future design explicitly defines and authorizes such a dependency.

## 9. Security-Monitoring Flows

### F-15 — Security Event Collection

**Sources:** A-001, A-002, A-003, A-004, A-005, A-006, A-007, A-009, A-010, A-011, and A-017  
**Destination:** A-013 Log Collector  
**Diagram style:** Green dotted  
**Purpose:** Collect security-relevant events from monitored assets.  
**Examples:** Authentication, privilege, administrative, mission-control, telemetry-processing, gateway, simulator, external-interface, and network-security events.

Logical source mappings include:

```text
A-001 → A-013  Security Events
A-002 → A-013  Authentication Events
A-003 → A-013  Privileged Access Events
A-004 → A-013  Administrative Session Events
A-005 → A-013  Mission Application Events
A-006 → A-013  Mission Control Events
A-007 → A-013  Telemetry Processing Events
A-009 → A-013  Gateway Security Events
A-010 → A-013  External Interface Events
A-011 → A-013  Simulator Security Events
A-017 → A-013  Network Security Events
```

F-15 is one logical monitoring category that represents several source-to-collector connections. It is not a single operational data path.

### F-16 — Centralized Log Ingestion

**Source:** A-013 Log Collector  
**Destination:** A-012 SIEM Platform  
**Diagram style:** Green solid  
**Purpose:** Forward collected events for normalization, correlation, alerting, and analysis.  
**Security considerations:** Integrity, availability, confidentiality, access control, and pipeline monitoring.

### F-17 — Security Evidence Retention

**Source:** A-012 SIEM Platform  
**Destination:** A-018 Assessment Evidence Repository  
**Diagram style:** Green solid  
**Purpose:** Retain selected logs, alerts, reports, and evidence for assessment and investigation.  
**Security considerations:** Confidentiality, integrity, retention control, access control, availability, and chain of custody.

> A-013 is not part of the normal command path. It collects observability data from the command path and other monitored components.

## 10. Cross-Cutting Service Flows

### F-18 — Configuration Baseline

**Source:** A-014 Configuration Baseline Repository  
**Destinations:** A-004, A-005, A-006, and A-009, where authorized  
**Diagram style:** Gold dashed  
**Purpose:** Provide approved configuration references and support configuration-drift detection.  
**Security considerations:** Integrity, authorization, approval, version control, accountability, and availability.

### F-19 — Backup and Recovery

**Sources:** A-005, A-006, A-007, A-008, A-011, A-012, A-013, and A-018  
**Destination:** A-015 Backup and Recovery Storage  
**Diagram style:** Gold dashed  
**Purpose:** Protect selected system, configuration, mission, monitoring, and evidence data for recovery.  
**Security considerations:** Confidentiality, integrity, availability, separation, retention, restoration testing, and access control.

### F-20 — Time Synchronization

**Source:** A-016 Time Synchronization Service  
**Destinations:** Mission and security assets  
**Diagram style:** Gold dashed  
**Purpose:** Provide a consistent time reference for operations, logs, event correlation, and investigations.  
**Security considerations:** Integrity, availability, source authentication, drift monitoring, and fallback behavior.

### F-21 — Policy Enforcement

**Source:** A-017 Network Security Controls  
**Destination:** Zone boundaries and controlled network paths  
**Diagram style:** Gold dashed  
**Purpose:** Enforce segmentation, allow or deny connections, and apply network-security policies.  
**Security considerations:** Policy integrity, change control, availability, logging, and resistance to unauthorized modification.

## 11. Trust Boundaries

### TB-01 — User Access / Enterprise Support

Separates the User Access Zone and Enterprise / Support Zone. Primary flow: F-01.

### TB-02 — Enterprise Support / Administrative Access

Separates the Enterprise / Support Zone and Administrative Access Zone. Primary flow: F-02.

### TB-03 — Administrative Access / Mission Operations

Separates the Administrative Access Zone and Mission Operations Zone. Primary flows: F-03 and F-04.

### TB-04 — Mission Operations / Ground Interface

Separates the Mission Operations Zone and Ground Interface Zone. Primary flows: F-06, F-09, F-13, and F-14.

### TB-05 — Ground Interface / Simulation

Separates the Ground Interface Zone and Simulation Zone. Primary flows: F-07 and F-08.

### TB-06 — Mission Operations / Security Monitoring

Separates the Mission Operations Zone and Security Monitoring Zone. Primary flow: F-15.

### TB-07 — Ground Interface / Third-Party Provider

Separates A-009 and A-010. Primary flows: F-13 and F-14.

### TB-08 — Cross-Cutting Services / Protected Assets

Separates shared services from the assets they support. Primary flows: F-18 through F-21.

## 12. Operational and Logging Paths

### Authentication path

```text
A-001 → A-002 → A-003
```

### Privileged administration path

```text
A-003 → A-004 → A-005
```

### Mission-command path

```text
A-005 → A-006 → A-009 → A-011
```

### Telemetry path

```text
A-011 → A-009 → A-007 → A-005
                         └→ A-008
```

### Security-monitoring path

```text
Monitored assets → A-013 → A-012 → A-018
```

The monitoring path observes operational components; it does not carry normal mission commands.

## 13. Diagram Traceability

The Architecture Overview does not need to display F-01 through F-21 beside every connector. The visible labels, colors, line styles, source assets, and destination assets provide the visual representation. This document provides the formal identifiers used for assessment traceability.

## 14. Initial Security Considerations

The following issues should be examined in the threat-model and risk-assessment document:

- compromise of A-001 and theft of operator credentials;
- authentication bypass or identity-provider compromise;
- PAM policy bypass or unauthorized privilege approval;
- bastion bypass or uncontrolled administrative access;
- unauthorized mission-command creation or transmission;
- telecommand injection, modification, or replay;
- telemetry manipulation, malformed input, or denial of service;
- compromise of A-009 Ground Station Gateway;
- compromise of the third-party provider interface;
- loss, suppression, or manipulation of security events;
- incorrect or inconsistent system time;
- configuration drift or unauthorized baseline changes;
- backup compromise or unsafe restoration;
- unauthorized network-policy changes;
- insufficient isolation of the Satellite Simulator;
- unauthorized access to assessment evidence;
- failure of monitoring or recovery capabilities.

These are initial considerations, not a completed threat model or risk assessment.

## 15. Traceability to Later Documents

This document provides inputs to:

### Document 05 — Threat Model and Risk Assessment

- asset-to-threat mapping;
- flow-based threat identification;
- trust-boundary analysis;
- impact and likelihood assessment;
- initial risk register.

### Document 06 — Security Requirements and Control Mapping

- access-control requirements;
- authentication requirements;
- logging and monitoring requirements;
- command and telemetry protection requirements;
- backup and recovery requirements;
- configuration-management requirements;
- network-segmentation requirements.

### Document 07 — Assessment Procedures and Evidence Plan

- evidence sources;
- expected logs;
- configuration evidence;
- test cases;
- assessment observations;
- control-verification procedures.

## 16. Limitations and Disclaimer

This document is a fictional educational artifact. It does not represent a real satellite, ground station, Mission Operations Center, service provider, organization, operational command system, or production cybersecurity architecture.

The assets, zones, labels, flows, and controls are simplified for educational use. A real mission would require mission-specific systems engineering, cybersecurity engineering, safety analysis, protocol selection, cryptographic design, operational approval, testing, validation, and authorization.

Referencing NIST, CCSDS, SPARTA, or other frameworks does not imply certification, compliance, or approval.

## 17. References

- NIST IR 8401, *Satellite Ground Segment: Applying the Cybersecurity Framework to Satellite Command and Control*.
- NIST SP 800-30, *Guide for Conducting Risk Assessments*.
- NIST SP 800-207, *Zero Trust Architecture*.
- CCSDS 350.0-G-3, *The Application of Security to CCSDS Protocols*.
- CCSDS 355.0-B-2, *Space Data Link Security Protocol*.
- Aerospace Corporation, *Space Segment Cybersecurity Profile*.
- Aerospace Corporation, SPARTA framework.
