# ThreatMesh: A Multi-Agent Threat Intelligence and Security Research Assistant

## Kaggle AI Agents Intensive Capstone Project

### Problem

Security analysts spend substantial time manually collecting, validating, correlating, and reporting threat intelligence information.

Tasks such as CVE research, ATT&CK mapping, and report generation often require switching between multiple tools and intelligence sources.

ThreatMesh addresses this challenge through a coordinated multi-agent architecture that automates these workflows while incorporating security controls and evaluation mechanisms.

---

## Solution

ThreatMesh is a Multi-Agent Threat Intelligence Platform built using Google ADK.

The platform uses specialized agents that collaborate to analyze vulnerabilities, enrich threat intelligence, map findings to MITRE ATT&CK techniques, generate intelligence reports, and validate outputs.

---

## Architecture

### Agents

* Coordinator Agent
* CVE Analysis Agent
* IOC Investigation Agent
* ATT&CK Mapping Agent
* Report Generator Agent
* Security Reviewer Agent

### Skills

* CVE Analysis Skill
* IOC Lookup Skill
* ATT&CK Mapping Skill
* Report Generation Skill

### MCP Resources

* NVD
* CISA KEV
* MITRE ATT&CK

### Database

PostgreSQL stores:

* Requests
* Analysis Results
* ATT&CK Mappings
* Agent Executions
* Reports
* Audit Logs

---

## Security Design

ThreatMesh incorporates security-by-design principles:

* Input Validation
* Tool Validation
* Least Privilege
* Human-in-the-Loop Approval
* Audit Logging
* MCP Validation
* Agent Isolation

Threats addressed include:

* Prompt Injection
* Tool Abuse
* Hallucinations
* Data Poisoning
* Secrets Exposure

---

## Evaluation Strategy

ThreatMesh includes an evaluation layer that measures:

* Response Accuracy
* ATT&CK Mapping Quality
* Report Completeness
* Agent Reliability
* Processing Performance

Agent execution metrics are collected through observability mechanisms and persisted for analysis.

---

## Expected User Workflow

1. Submit CVE request
2. Coordinator selects agents
3. CVE analysis performed
4. ATT&CK mapping generated
5. Report produced
6. Security validation performed
7. Results stored and displayed

---

## Technologies

* Google ADK
* Gemini
* MCP
* Agent Skills
* PostgreSQL
* Streamlit
* Docker
* Cloud Run

---

## Lessons Applied From Course

### Day 2

* MCP
* Tool Interoperability

### Day 3

* Agent Skills
* Multi-Agent Design

### Day 4

* Secure Agent Engineering
* Human-in-the-Loop Controls

### Day 5

* Agent Evaluation
* Observability
* Performance Measurement

---

## Future Roadmap

* IOC Enrichment Expansion
* Threat Actor Profiling
* Malware Analysis
* Additional Threat Intelligence Sources
* Authentication
* Multi-User Support

---

## Conclusion

ThreatMesh demonstrates how secure, observable, and evaluatable multi-agent systems can automate cybersecurity workflows while applying the core concepts taught throughout the Kaggle AI Agents Intensive course.
