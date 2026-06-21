# ThreatMesh System Architecture

## Project Overview

ThreatMesh is a Multi-Agent Threat Intelligence Platform designed to assist Threat Intelligence Teams in analyzing vulnerabilities, investigating Indicators of Compromise (IOCs), mapping threats to MITRE ATT&CK techniques, and generating actionable intelligence reports.

The platform leverages Google Agent Development Kit (ADK), Agent Skills, Model Context Protocol (MCP), PostgreSQL, Docker, and Cloud Run to provide a secure and scalable agentic workflow.

---

## Business Problem

Threat Intelligence Analysts spend significant time:

* Researching CVEs
* Investigating suspicious IPs, domains, URLs, and hashes
* Mapping findings to MITRE ATT&CK
* Preparing executive and technical reports
* Correlating information from multiple threat intelligence sources

These repetitive activities reduce analyst productivity and increase investigation time.

ThreatMesh automates these workflows using specialized AI agents.

---

## Target Users

### Primary Users

* Threat Intelligence Teams

### Secondary Users

* Security Operations Center (SOC) Analysts
* Vulnerability Management Teams
* Security Researchers

---

## Solution Overview

ThreatMesh provides an agent-driven workflow where specialized agents collaborate to analyze cybersecurity threats and generate intelligence reports.

The system coordinates:

* Vulnerability Analysis
* IOC Investigation
* ATT&CK Mapping
* Report Generation
* Security Validation

through a centralized orchestration layer.

---

## Core Workflow

1. User submits a threat intelligence request.
2. Coordinator Agent analyzes the request.
3. Relevant specialized agents are invoked.
4. Agents execute skills and retrieve intelligence.
5. Findings are aggregated.
6. Security Reviewer validates output.
7. Report Generator creates final reports.
8. Results are displayed and stored.

---

## System Components

### Frontend Layer

Technology:

* Streamlit

Responsibilities:

* User input
* Report visualization
* Investigation dashboard
* Export functionality

---

### Agent Layer

Technology:

* Google ADK

Components:

* Coordinator Agent
* CVE Analysis Agent
* IOC Investigation Agent
* ATT&CK Mapping Agent
* Report Generator Agent
* Security Reviewer Agent

Responsibilities:

* Task routing
* Analysis
* Collaboration
* Report generation

---

### Skills Layer

Reusable capabilities:

* CVE Analysis Skill
* IOC Lookup Skill
* ATT&CK Mapping Skill
* Report Generation Skill

Responsibilities:

* Encapsulate repeatable logic
* Reduce prompt duplication
* Improve maintainability

---

### MCP Layer

Purpose:
Provide standardized access to threat intelligence resources.

Data Sources:

* NVD
* CISA KEV
* MITRE ATT&CK

Responsibilities:

* Context retrieval
* Tool exposure
* Resource access

---

### Database Layer

Technology:

* PostgreSQL

Responsibilities:

* Request storage
* Investigation storage
* Report storage
* Audit logging

---

### Security Layer

Responsibilities:

* Input validation
* Tool validation
* Audit logging
* Human approval workflow
* Least privilege enforcement

---

## High-Level Architecture Diagram

User
↓
Streamlit UI
↓
Coordinator Agent
↓
├── CVE Analysis Agent
├── IOC Investigation Agent
├── ATT&CK Mapping Agent
├── Report Generator Agent
└── Security Reviewer Agent
↓
Skills Layer
↓
MCP Layer
↓
Threat Intelligence Sources
↓
PostgreSQL Database

---

## Request Processing Flow

User Request
↓
Input Validation
↓
Coordinator Agent
↓
Agent Selection
↓
Skill Execution
↓
MCP Context Retrieval
↓
Result Aggregation
↓
Security Review
↓
Report Generation
↓
Persistence
↓
User Response

---

## Technology Stack

### Frontend

* Streamlit

### Agent Framework

* Google ADK

### LLM

* Gemini

### Agent Skills

* ADK Skills

### Context Layer

* MCP

### Database

* PostgreSQL

### Containerization

* Docker

### Deployment

* Google Cloud Run

### Version Control

* Git
* GitHub

---

## Non-Functional Requirements

### Security

* Secure handling of user inputs
* Auditability
* Validation of external data

### Scalability

* Modular agent architecture
* Extensible skill framework

### Reliability

* Error handling
* Logging
* Graceful degradation

### Maintainability

* Documentation-first approach
* ADR-based decision tracking

---

## Future Enhancements

* Additional threat intelligence feeds
* Malware analysis agents
* Threat actor profiling
* PDF report exports
* SOC integration
* Multi-user support
* Advanced analytics dashboards
