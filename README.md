# ThreatMesh

## A Multi-Agent Threat Intelligence and Security Research Assistant

ThreatMesh is a multi-agent cybersecurity platform that automates vulnerability analysis, threat intelligence enrichment, MITRE ATT&CK mapping, security validation, and intelligence report generation.

Built as a Kaggle AI Agents Intensive Capstone Project, ThreatMesh demonstrates modern AI agent engineering concepts including Google ADK, Agent Skills, MCP, secure agent design, evaluation, PostgreSQL persistence, Docker deployment, and Google Cloud Run deployment.

---

## Problem Statement

Threat Intelligence Analysts spend significant time:

* Researching CVEs
* Mapping vulnerabilities to MITRE ATT&CK
* Gathering intelligence from multiple sources
* Producing executive and technical reports
* Validating findings before distribution

These manual workflows reduce analyst productivity and increase investigation time.

ThreatMesh automates these processes using specialized AI agents coordinated through a centralized orchestration layer.

---

## Key Features

### Multi-Agent Architecture

* Coordinator Agent
* CVE Analysis Agent
* IOC Investigation Agent (Optional MVP Extension)
* ATT&CK Mapping Agent
* Report Generator Agent
* Security Reviewer Agent

### Threat Intelligence Capabilities

* CVE Analysis
* MITRE ATT&CK Mapping
* Executive Report Generation
* Security Validation
* Audit Logging
* Agent Observability

### Security-by-Design

* Input Validation
* Tool Validation
* Least Privilege
* Human-in-the-Loop Approval
* Audit Logging
* MCP Validation

---

## Technology Stack

| Component        | Technology       |
| ---------------- | ---------------- |
| Frontend         | Streamlit        |
| Agent Framework  | Google ADK       |
| LLM              | Gemini           |
| Skills           | ADK Agent Skills |
| Context Layer    | MCP              |
| Database         | PostgreSQL       |
| Containerization | Docker           |
| Deployment       | Google Cloud Run |
| Version Control  | GitHub           |

---

## Architecture

User
↓
Streamlit
↓
Coordinator Agent
↓
Specialized Agents
↓
Skills Layer
↓
MCP Layer
↓
Threat Intelligence Sources
↓
PostgreSQL

Threat Intelligence Sources:

* NVD
* CISA KEV
* MITRE ATT&CK

---

## MVP Scope

### Included

* CVE Analysis
* ATT&CK Mapping
* Executive Report Generation
* Security Validation
* PostgreSQL Persistence
* Audit Logging

### Optional Extensions

* IOC Investigation
* Technical Reports

### Deferred

* Malware Analysis
* Threat Actor Profiling
* RAG
* Vector Databases
* Authentication
* RBAC
* SIEM Integrations

---

## Project Status

Architecture Phase: Complete

Implementation Phase: Planned

Current Version: v1 Architecture Freeze

---

## Kaggle Capstone Alignment

ThreatMesh demonstrates:

* Multi-Agent Systems
* Agent Skills
* MCP Integration
* Secure Agent Design
* Agent Evaluation
* PostgreSQL Persistence
* Docker Deployment
* Cloud Run Deployment

---

## License

MIT License