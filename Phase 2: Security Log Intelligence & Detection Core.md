“This phase is the core of my Splunk project. I onboarded real authentication logs and treated them like a live security data source, not just a file upload. I validated timestamps and fields, then used SPL to analyze login behavior, failures, trends, and anomalies. After that, I reframed these searches into detection-style logic such as brute-force attempts, multi-user targeting, and off-hours activity. This phase shows how raw logs are converted into actionable security insights, similar to how a SOC operates in real environments.”

___

#  Data Source Selection & Context Definition

## Objective
The goal of this step is to clearly understand and define the security context of the available JSON log file before ingesting it into Splunk. This ensures the data is treated as a meaningful security data source rather than just a raw file.

---

## Data Source Overview

- The data source used in this project is a **structured JSON log file**
- The log contains **authentication-related security events**
- These events are relevant for **SOC monitoring and detection use cases**

### Security Relevance
The JSON logs include information such as:
- User authentication attempts
- Successful and failed login events
- Source IP addresses
- Event timestamps
---

<img width="1907" height="627" alt="Splunk4" src="https://github.com/user-attachments/assets/86f002c9-0309-4cc0-a38c-915db2797110" />

<img width="1876" height="882" alt="Splunk5" src="https://github.com/user-attachments/assets/73f5e2c7-9503-48bf-9737-34feac69635d" />



