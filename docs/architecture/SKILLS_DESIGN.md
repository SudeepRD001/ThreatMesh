# ThreatMesh Skills Design

## Skills Overview

ThreatMesh uses reusable Agent Skills to encapsulate domain-specific cybersecurity functionality.

Skills provide modular, reusable capabilities that can be invoked by one or more agents without duplicating logic.

### Design Principles

* Single Responsibility
* Reusability
* Security by Design
* Testability
* Maintainability

---

# CVE Analysis Skill

## Purpose

Analyze Common Vulnerabilities and Exposures (CVEs) and generate actionable security intelligence.

## Consuming Agent

* CVE Analysis Agent

## Inputs

### Required

* CVE Identifier

Example:

CVE-2026-1234

## Outputs

* CVE Summary
* CVSS Score
* Severity
* Exploitability Assessment
* Affected Systems
* Mitigation Recommendations

## Logic Flow

1. Validate CVE format.
2. Retrieve NVD information.
3. Retrieve CISA KEV information.
4. Analyze severity.
5. Evaluate exploitability.
6. Generate recommendations.
7. Return structured output.

## External Dependencies

* NVD
* CISA KEV
* Threat Intelligence MCP

## Failure Conditions

* Invalid CVE ID
* NVD unavailable
* Missing vulnerability data

---

# IOC Lookup Skill

## Purpose

Investigate Indicators of Compromise (IOCs) and assess potential risk.

## Consuming Agent

* IOC Investigation Agent

## Inputs

### Supported Types

* IP Address
* Domain
* URL
* File Hash

## Outputs

* IOC Summary
* Reputation Assessment
* Risk Score
* Threat Classification
* Recommended Actions

## Logic Flow

1. Validate IOC format.
2. Identify IOC type.
3. Query threat intelligence resources.
4. Analyze results.
5. Calculate risk score.
6. Generate recommendations.
7. Return structured output.

## External Dependencies

* Threat Intelligence MCP

## Failure Conditions

* Invalid IOC format
* Lookup service unavailable
* Incomplete intelligence data

---

# ATT&CK Mapping Skill

## Purpose

Map investigation findings to MITRE ATT&CK tactics and techniques.

## Consuming Agent

* ATT&CK Mapping Agent

## Inputs

* CVE Analysis Results
* IOC Analysis Results

## Outputs

* ATT&CK Tactics
* ATT&CK Techniques
* Technique Descriptions
* Mapping Justification

## Logic Flow

1. Analyze investigation findings.
2. Identify attacker behaviors.
3. Match behaviors to ATT&CK framework.
4. Generate mapping explanations.
5. Return ATT&CK references.

## External Dependencies

* MITRE ATT&CK
* Threat Intelligence MCP

## Failure Conditions

* No matching techniques
* Missing ATT&CK references

---

# Report Generation Skill

## Purpose

Generate structured threat intelligence reports from investigation findings.

## Consuming Agents

* Report Generator Agent

## Inputs

* CVE Findings
* IOC Findings
* ATT&CK Findings
* Investigation Metadata

## Outputs

### Executive Report

Management-oriented summary.

### Technical Report

Analyst-oriented report.

## Logic Flow

1. Collect investigation findings.
2. Organize findings.
3. Create executive summary.
4. Create technical report.
5. Generate recommendations.
6. Format output.
7. Return final report.

## External Dependencies

* Report Templates

## Failure Conditions

* Missing findings
* Incomplete investigation data

---

# Skill Reusability Strategy

## Modular Design

Each skill performs a single task.

## Shared Usage

Multiple agents may consume the same skill.

## Independent Testing

Skills can be tested without agent orchestration.

## Extensibility

Additional skills can be introduced without changing existing agents.

---

# Skill Security Considerations

## Input Validation

All inputs are validated before processing.

## Output Validation

Structured outputs are validated before returning results.

## External Resource Validation

Responses from external sources are verified.

## Least Privilege

Skills receive only the resources required to perform their tasks.

## Audit Logging

Skill execution events are recorded for investigation and troubleshooting.

---

# Future Skills

## Malware Analysis Skill

Analyze malware indicators and behavior.

## Threat Actor Profiling Skill

Generate threat actor intelligence.

## Campaign Correlation Skill

Correlate incidents across investigations.

## Security Control Recommendation Skill

Recommend defensive controls based on findings.

## Threat Hunting Skill

Generate threat hunting hypotheses and queries.