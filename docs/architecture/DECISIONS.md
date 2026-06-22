# ThreatMesh Architecture Decisions

This document records major architectural decisions made during the design and implementation of ThreatMesh.

---

# ADR-001

## Decision

Use Google ADK (Agent Development Kit) for agent orchestration.

## Reason

* Direct alignment with Kaggle Capstone requirements.
* Native support for multi-agent workflows.
* Demonstrates course concepts from Day 3.

## Status

Accepted

---

# ADR-002

## Decision

Build ThreatMesh as a Multi-Agent Threat Intelligence Platform.

## Reason

* Demonstrates agent collaboration.
* Maps directly to real-world cybersecurity workflows.
* Covers multiple course concepts in a single solution.

## Status

Accepted

---

# ADR-003

## Decision

Target Threat Intelligence Teams as the primary users.

## Reason

* Combines vulnerability analysis, IOC investigation, and intelligence reporting.
* Provides a clear business use case.
* Avoids overly broad SOC workflows.

## Status

Accepted

---

# ADR-004

## Decision

Support CVE Analysis, IOC Investigation, and Threat Intelligence Reporting in a single workflow.

## Reason

* Demonstrates meaningful agent collaboration.
* Creates a stronger end-to-end solution.
* Increases technical depth without expanding project scope excessively.

## Status

Accepted

---

# ADR-005

## Decision

Use Streamlit for the user interface.

## Reason

* Fast development.
* Suitable for demonstrations.
* Minimizes frontend complexity.
* Allows focus on agent architecture.

## Status

Accepted

---

# ADR-006

## Decision

Use PostgreSQL as the primary database.

## Reason

* Production-oriented architecture.
* Supports future scalability.
* Aligns with enterprise software practices.

## Status

Accepted

---

# ADR-007

## Decision

Use real threat intelligence sources instead of mock data.

## Reason

* Improves realism.
* Demonstrates practical applicability.
* Increases project credibility.

## Initial Sources

* NVD
* CISA KEV
* MITRE ATT&CK

## Status

Accepted

---

# ADR-008

## Decision

Use Docker for local development and testing.

## Reason

* Consistent development environment.
* Simplifies deployment.
* Improves reproducibility.

## Status

Accepted

---

# ADR-009

## Decision

Deploy the final application on Google Cloud Run.

## Reason

* Demonstrates deployability.
* Aligns with course content.
* Low operational overhead.

## Status

Accepted

---

# ADR-010

## Decision

Adopt a Documentation-First Development Approach.

## Reason

* Reduces implementation risk.
* Improves project organization.
* Enables architecture validation before coding.

## Status

Accepted

---

# ADR-011

## Decision

Create dedicated architecture documents before implementation.

## Documents

* SYSTEM_ARCHITECTURE.md
* AGENT_DESIGN.md
* SKILLS_DESIGN.md
* MCP_DESIGN.md
* DATABASE_DESIGN.md
* SECURITY_DESIGN.md
* DEPLOYMENT_DESIGN.md

## Reason

* Enables structured design reviews.
* Simplifies implementation planning.
* Improves Kaggle writeup quality.

## Status

Accepted

---

# ADR-012

## Decision

Implement security controls as first-class architecture components.

## Planned Controls

* Input Validation
* Tool Validation
* Audit Logging
* Least Privilege
* Human-in-the-Loop Approval

## Reason

* Directly incorporates Day 4 learning.
* Strengthens project trustworthiness.
* Demonstrates secure agent design.

## Status

Accepted

---

# ADR-013

## Decision

Store agent execution traces separately from audit logs.

## Reason

Improves observability, debugging, evaluation, and security auditing.

## Status

Accepted

---

# ADR-014

## Decision

Adopt a Security-by-Design architecture for ThreatMesh.

## Reason

Security controls must be embedded throughout the agent lifecycle rather than added after implementation.

## Status

Accepted

---