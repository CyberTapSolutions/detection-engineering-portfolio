# Detection Engineering Portfolio

A hands on cybersecurity portfolio focused on detection engineering, threat hunting, security operations, threat intelligence, and security automation.

This repository documents my development of detection engineering capabilities through practical security scenarios using Kusto Query Language (KQL), Python, Microsoft security technologies, MITRE ATT&CK, and threat intelligence workflows.

The goal of this portfolio is not simply to create detection queries. Each project follows the detection lifecycle from identifying adversary behavior through developing, testing, tuning, and documenting detection logic.

## Detection Engineering Lifecycle

Threat Behavior → Telemetry → Detection Logic → Alert → Investigation → Tuning → Coverage Decision

## Portfolio Objectives

This portfolio focuses on developing practical experience in:

* KQL based security analytics
* Detection engineering
* Threat hunting
* SIEM and EDR investigation
* MITRE ATT&CK mapping
* Detection tuning and false positive analysis
* Threat intelligence and IOC analysis
* Python security automation
* Detection coverage analysis
* Incident investigation
* AI assisted security workflows

## Repository Structure

### detections

Detection logic, KQL queries, testing methodology, tuning decisions, and validation results.

### threat-hunting

Documented threat hunting scenarios, hypotheses, queries, findings, and investigation workflows.

### attack-coverage

MITRE ATT&CK mappings, detection coverage analysis, identified gaps, and coverage decisions.

### threat-intelligence

IOC analysis, threat intelligence workflows, MISP integration, and malicious infrastructure analysis.

### automation

Python based security automation supporting detection engineering, threat analysis, enrichment, and investigation.

### notebooks

Jupyter notebooks used for security data analysis, detection testing, and false positive analysis.

### incident-simulations

Documented security scenarios demonstrating investigation, detection, containment, and remediation workflows.

### documentation

Detection engineering methodology, portfolio standards, architecture, and supporting documentation.

## Detection Portfolio

| ID | Detection | MITRE ATT&CK | Status |
|---|---|---|---|
| DET-001 | Password Spraying | T1110.003 | Planned |
| DET-002 | Brute Force Authentication | T1110 | Planned |
| DET-003 | Suspicious Authentication | T1078 | Planned |
| DET-004 | Privileged Role Change | T1098 | Planned |
| DET-005 | Suspicious PowerShell | T1059.001 | Planned |

## Detection Documentation Standard

Each detection will document:

1. Detection objective
2. Threat hypothesis
3. MITRE ATT&CK mapping
4. Required telemetry
5. KQL detection logic
6. Testing methodology
7. Investigation workflow
8. False positive analysis
9. Tuning decisions
10. Known limitations
11. Coverage decision
12. Validation evidence

## Technologies

* Microsoft Sentinel
* Kusto Query Language (KQL)
* Microsoft security telemetry
* Python
* PowerShell
* MITRE ATT&CK
* MISP
* Git
* GitHub
* Visual Studio Code
* Jupyter

## Current Focus

The first phase of this portfolio focuses on identity based detection engineering and KQL.

The first detection under development is:

**DET-001: Password Spraying**

MITRE ATT&CK: **T1110.003 Password Spraying**

The project will examine authentication telemetry to identify password spraying behavior, develop KQL based detection logic, analyze false positives, tune detection thresholds, and document the resulting detection coverage.