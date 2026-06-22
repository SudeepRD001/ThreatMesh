# ThreatMesh Deployment Design

## Deployment Overview

ThreatMesh follows a containerized deployment architecture designed for:

* Local Development
* Reproducible Testing
* Cloud Deployment
* Cost Efficiency
* Simplicity

The deployment strategy prioritizes developer productivity while remaining production-oriented.

---

# Deployment Goals

## Goal 1

Provide a consistent local development environment.

---

## Goal 2

Enable reproducible testing using Docker.

---

## Goal 3

Deploy the platform to Google Cloud Run.

---

## Goal 4

Minimize infrastructure management overhead.

---

## Goal 5

Support future scalability.

---

# Local Development Architecture

Developer
↓
Streamlit Application
↓
ADK Agents
↓
Skills Layer
↓
MCP Server
↓
PostgreSQL

---

## Local Components

### Streamlit

Frontend interface.

---

### Agent Runtime

Google ADK agents.

---

### MCP Server

Threat Intelligence MCP Server.

---

### PostgreSQL

Persistent storage.

---

# Docker Architecture

ThreatMesh uses Docker for local development and deployment consistency.

---

## Container Strategy

### Application Container

Contains:

* Streamlit
* ADK Agents
* Skills
* MCP Components

---

### Database Container

Contains:

* PostgreSQL

---

## Benefits

* Environment consistency
* Simplified onboarding
* Easier deployment
* Isolation of dependencies

---

# Docker Compose Design

## Services

### threatmesh-app

Purpose:

Run:

* Streamlit UI
* ADK Agents
* Skills
* MCP Integrations

---

### postgres

Purpose:

Provide persistent storage.

---

## High-Level Flow

threatmesh-app
↓
postgres

---

# Streamlit Deployment

## Purpose

Provide a simple and interactive user interface.

---

## Responsibilities

* Accept investigation requests
* Display analysis results
* Display reports
* Display validation results

---

## User Workflow

Submit Request
↓
Agent Processing
↓
Report Generation
↓
Result Display

---

# PostgreSQL Deployment

## Purpose

Persist application data.

---

## Stored Data

* Threat Requests
* CVE Analysis
* IOC Analysis
* Agent Executions
* Reports
* Audit Logs

---

## Persistence Strategy

Docker Volume

Purpose:

Prevent data loss during container restarts.

---

# Cloud Run Deployment

## Purpose

Provide serverless deployment for demonstrations and production-style operation.

---

## Architecture

User
↓
Cloud Run
↓
ThreatMesh Application
↓
PostgreSQL

---

## Cloud Run Benefits

* Fully managed
* Auto-scaling
* HTTPS support
* Minimal operational overhead

---

## Deployment Flow

GitHub
↓
Container Build
↓
Container Registry
↓
Cloud Run
↓
User Access

---

# Environment Variables

## Purpose

Separate configuration from code.

---

## Required Variables

### GOOGLE_API_KEY

Gemini access.

---

### DATABASE_URL

PostgreSQL connection string.

---

### MCP_SERVER_URL

Threat Intelligence MCP endpoint.

---

### LOG_LEVEL

Application logging level.

---

## Security Rules

Never:

* Hardcode credentials
* Commit secrets
* Store API keys in source code

---

# Monitoring and Logging

## Objectives

* Troubleshooting
* Security Auditing
* Performance Monitoring

---

## Logged Events

### Application Events

* Startup
* Shutdown
* Errors

---

### Agent Events

* Agent Execution
* Agent Failures

---

### MCP Events

* Resource Access
* Tool Execution

---

### Security Events

* Validation Failures
* Approval Decisions

---

## Log Storage

### Local

Console Logs

---

### Cloud

Cloud Run Logs

---

# CI/CD Strategy

## Initial Capstone Strategy

Manual Deployment

Reason:

* Simplicity
* Reduced complexity
* Faster development

---

## Future Strategy

GitHub Actions

Workflow:

Code Push
↓
Build
↓
Test
↓
Deploy

---

# Backup and Recovery

## Database Backup

Future enhancement.

---

## Recovery Strategy

Rebuild application container from source.

Restore PostgreSQL backup.

---

# Cost Considerations

## Development Environment

Cost:

Free

Components:

* Local Docker
* PostgreSQL
* Streamlit

---

## Cloud Deployment

Target:

Google Cloud Run Free Tier

---

## Cost Optimization

* Scale-to-zero
* Minimal resource allocation
* Shared infrastructure

---

# Reliability Strategy

## Error Handling

Graceful failure handling.

---

## Agent Failures

Coordinator continues where possible.

---

## MCP Failures

Fallback error responses.

---

## Database Failures

Application reports service degradation.

---

# Scalability Strategy

## Current Scope

Single-user demonstration environment.

---

## Future Scope

Multi-user deployment.

---

## Scaling Options

* Cloud SQL
* Load Balancing
* Managed PostgreSQL
* Horizontal Scaling

---

# Future Deployment Enhancements

## GitHub Actions CI/CD

Automated deployment pipeline.

---

## Cloud SQL

Managed PostgreSQL.

---

## Container Registry Automation

Automated image publishing.

---

## Authentication Layer

User authentication and authorization.

---

## Multi-Environment Deployment

* Development
* Staging
* Production

---

## Monitoring Dashboard

Operational observability.

---

# Deployment Success Criteria

ThreatMesh deployment architecture is successful when:

* Developers can run the platform locally.
* Docker provides consistent environments.
* PostgreSQL persists investigation data.
* Cloud Run hosts the application successfully.
* Environment variables protect secrets.
* Logs support troubleshooting and auditing.
* The platform can be demonstrated reliably.