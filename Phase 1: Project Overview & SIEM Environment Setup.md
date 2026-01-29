# Phase 1 – Project Overview & SIEM Environment Setup

## Let me establish the Goal:

- Why this project exists
- What problems it focuses on
- How the SIEM environment is deployed

---

## Project Objective (SplunkSight)
SplunkSight is a hands-on project focused on learning and demonstrating:

### SIEM Fundamentals
This project focuses on understanding how a SIEM works at a practical level, including:
- How logs are collected, indexed, and stored
- How searches are written to extract meaningful information
- How events are correlated to identify suspicious or abnormal behavior

The intent is to understand **how Splunk functions as a SIEM**, not just how to click through the UI.

---

### Log Ingestion and Analysis
A core part of this project is working with real logs instead of sample data.

This includes:
- Ingesting logs from Windows and other systems
- Understanding log structure (fields, timestamps, sources)
- Writing searches to filter, aggregate, and analyze events
- Identifying patterns such as errors, failures, or unusual activity



---

### Security Visibility Using Real System Logs
Rather than simulated dashboards, the project focuses on gaining visibility from actual system-generated data.

This includes:
- Observing authentication activity
- Tracking system-level events
- Identifying behavior that could indicate misconfiguration, misuse, or attack activity

The scope is **security-relevant use cases**.

---

## Scope & Expectations
- Focus on **log-based detection and analysis**
- Emphasis on **security events**, not dashboards for business analytics
- All configurations are done manually to understand how Splunk works internally

---

## SIEM Environment Setup

### What Is Being Done
- Splunk Enterprise is installed on the **Windows host machine**

### Deployment Choice
- Splunk is **not** deployed as a virtual machine
- No Docker or container-based setup is used
- Splunk is kept separate from attacker or lab machines

### Reasoning (Brief)
- Simplifies setup and resource usage
- Provides stable performance for indexing and searching
- Allows direct access to Windows-based log sources
- Reflects common enterprise-style Splunk deployments

---
- Environment ready for:
  - Log ingestion
  - Search and analysis
  - Security-focused use cases in upcoming phases
