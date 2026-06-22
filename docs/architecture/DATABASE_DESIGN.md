# ThreatMesh Database Design

## Database Overview

ThreatMesh uses PostgreSQL as its primary persistence layer.

The database stores:

* Investigation requests
* Agent execution results
* CVE analysis findings
* IOC investigation findings
* Generated reports
* Audit logs

The design prioritizes:

* Simplicity
* Security
* Auditability
* Extensibility

for the Capstone MVP while remaining production-oriented.

---

# PostgreSQL Architecture

ThreatMesh follows a centralized PostgreSQL architecture.

User Request
↓
Agents
↓
Skills
↓
PostgreSQL

The database acts as the system of record for all investigations and generated intelligence.

---

# Entity Relationship Diagram

threat_requests
│
├── cve_analysis
│
├── ioc_analysis
│
├── agent_executions
│
└── reports

audit_logs

---

# Tables

## threat_requests

### Purpose

Store investigation requests submitted by users.

### Columns

| Column       | Type      |
| ------------ | --------- |
| id           | UUID      |
| request_type | VARCHAR   |
| user_input   | TEXT      |
| status       | VARCHAR   |
| created_at   | TIMESTAMP |
| updated_at   | TIMESTAMP |

### Example Request Types

* CVE Analysis
* IOC Investigation
* Threat Report

---

## cve_analysis

### Purpose

Store CVE investigation results.

### Columns

| Column     | Type      |
| ---------- | --------- |
| id         | UUID      |
| request_id | UUID      |
| cve_id     | VARCHAR   |
| cvss_score | NUMERIC   |
| severity   | VARCHAR   |
| summary    | TEXT      |
| mitigation | TEXT      |
| created_at | TIMESTAMP |

### Relationship

Many CVE analyses belong to one threat request.

---

## ioc_analysis

### Purpose

Store IOC investigation results.

### Columns

| Column          | Type      |
| --------------- | --------- |
| id              | UUID      |
| request_id      | UUID      |
| ioc_type        | VARCHAR   |
| ioc_value       | TEXT      |
| risk_score      | NUMERIC   |
| findings        | TEXT      |
| recommendations | TEXT      |
| created_at      | TIMESTAMP |

### Relationship

Many IOC investigations belong to one threat request.

---

## agent_executions

### Purpose

Track execution activity for all agents.

### Why This Table Exists

Provides:

* Observability
* Debugging
* Security auditing
* Agent performance analysis

### Columns

| Column            | Type      |
| ----------------- | --------- |
| id                | UUID      |
| request_id        | UUID      |
| agent_name        | VARCHAR   |
| execution_status  | VARCHAR   |
| execution_time_ms | INTEGER   |
| input_summary     | TEXT      |
| output_summary    | TEXT      |
| created_at        | TIMESTAMP |

### Example Agents

* Coordinator Agent
* CVE Analysis Agent
* IOC Investigation Agent
* ATT&CK Mapping Agent
* Report Generator Agent
* Security Reviewer Agent

---

## reports

### Purpose

Store generated intelligence reports.

### Columns

| Column          | Type      |
| --------------- | --------- |
| id              | UUID      |
| request_id      | UUID      |
| report_type     | VARCHAR   |
| report_content  | TEXT      |
| approval_status | VARCHAR   |
| created_at      | TIMESTAMP |

### Supported Report Types

* Executive Report
* Technical Report

---

## audit_logs

### Purpose

Maintain immutable security and operational audit records.

### Columns

| Column            | Type      |
| ----------------- | --------- |
| id                | UUID      |
| event_type        | VARCHAR   |
| event_source      | VARCHAR   |
| event_description | TEXT      |
| severity          | VARCHAR   |
| created_at        | TIMESTAMP |

### Example Events

* Agent Invoked
* MCP Resource Accessed
* Validation Failure
* Report Approved
* Report Rejected

---

# Relationships

## threat_requests → cve_analysis

One-to-Many

---

## threat_requests → ioc_analysis

One-to-Many

---

## threat_requests → agent_executions

One-to-Many

---

## threat_requests → reports

One-to-Many

---

## audit_logs

Independent audit trail.

No cascading deletes.

---

# Data Retention Strategy

## Investigation Data

Retained for demonstration and reporting purposes.

---

## Reports

Retained indefinitely.

---

## Audit Logs

Retained for security review and troubleshooting.

---

## Future Enhancement

Configurable retention policies.

---

# Security Considerations

## Principle of Least Privilege

Agents access only required data.

---

## Auditability

All agent activities are recorded.

---

## Input Validation

Only validated investigation requests are stored.

---

## Data Integrity

Foreign keys enforce relationship consistency.

---

## Secure Secrets Handling

Secrets are never stored in database tables.

Environment variables are used instead.

---

# Database Indexing Strategy

## threat_requests

Indexes:

* request_type
* status
* created_at

---

## cve_analysis

Indexes:

* cve_id
* severity

---

## ioc_analysis

Indexes:

* ioc_type
* risk_score

---

## agent_executions

Indexes:

* agent_name
* execution_status

---

## audit_logs

Indexes:

* event_type
* severity
* created_at

---

# Future Database Enhancements

## Threat Intelligence Cache

Reduce repeated external lookups.

---

## ATT&CK Mapping Storage

Persist ATT&CK mappings.

---

## Threat Actor Intelligence

Store threat actor profiles.

---

## Investigation History

Support advanced analytics and trend analysis.

---

## Multi-User Support

Enable organization-level deployments.