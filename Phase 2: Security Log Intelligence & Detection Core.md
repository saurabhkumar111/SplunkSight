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

# Log Ingestion into Splunk

The objective is to ingest a pre-analysed JSON authentication log file into Splunk and confirm that the data is successfully indexed and searchable.
---
---

## 1. Access Splunk Web
- Logged into Splunk Web interface
- Navigated to:
  **Settings → Add Data**

---

### 2. Select Data Input Method
- Chose **Upload** as the data input method

---

### 3. Select JSON Log File
- Browsed and selected the downloaded `.json` log file
- Proceeded to the next step after file selection
<img width="940" height="476" alt="image" src="https://github.com/user-attachments/assets/58150c2f-b628-43d9-aef9-3512e406eea4" />


---

### 4. Source Type Selection
- Allowed Splunk to auto-detect the source type
- Selected a JSON-compatible source type (`json` / `structured`)

---

### 5. Input Settings Configuration
- **Host**: Assigned a logical host value representing the log source
- **Index**: Selected the default `main` index
- **App Context**: Search & Reporting
<img width="1916" height="970" alt="Splunk7" src="https://github.com/user-attachments/assets/b4ce2ea4-ede6-45dc-b14f-5187dc89c9cb" />
---

### 6. Review and Submit
- Reviewed all input configurations
- Submitted the data input for indexing
<img width="1918" height="582" alt="Splunk8" src="https://github.com/user-attachments/assets/29b7bd71-4382-4a45-9a95-be5b1cd3412d" />


---

### 7. Ingestion Verification and validation

After submission, ingestion was verified by running a basic search. i.e. index=main

- Confirmed that events are visible in Splunk Search
- Verified that JSON events are indexed successfully
- Ensured no ingestion errors were present

<img width="1918" height="962" alt="Splunk10" src="https://github.com/user-attachments/assets/c0acdfed-9f48-4204-b914-8d5622f18d27" />


---

## Outcome
The JSON authentication log file was successfully ingested into Splunk and indexed in the `main` index. The data is now available for timestamp validation, field verification, and security-focused SPL analysis in subsequent steps.



