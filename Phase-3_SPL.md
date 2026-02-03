# SPL Validation (Indexing, Sourcetype & Timestamps)

## Objective
The objective of this phase is to validate that the ingested security logs are correctly indexed, properly parsed using the appropriate sourcetype, and accurately timestamped.
This phase uses targeted SPL searches to confirm data reliability before moving into detection and analysis use cases.

---

## Command 1 – Index Validation & Event Availability

### SPL Used
index=main host="security-log-source"


### What This Establishes
- Confirms that events are successfully indexed
- Verifies that the correct index (`main`) is being used
- Confirms that data is searchable and accessible

### Evidence
- Screenshot showing total event count (1,200 events)
- Timeline visible with events present
<img width="1917" height="970" alt="event visibility 1" src="https://github.com/user-attachments/assets/d2b1345c-76c3-45e2-845f-17c6fe5de0d0" />

---

## Command 2 – Timestamp Accuracy Validation (_time vs ts)

### SPL Used
index=main host="security-log-source"| table _time ts username auth_success



### What This Establishes
- Confirms Splunk `_time` matches original log timestamp (`ts`)
- Validates timezone normalization (UTC to local)
- Confirms accurate event-time extraction

### Evidence
- Screenshot showing `_time` and `ts` side by side
<img width="1947" height="977" alt="vlidation2" src="https://github.com/user-attachments/assets/b2523ef4-ecbd-4dc2-8182-10906b92e29c" />


---

## Command 3 – Time Distribution Check

### SPL Used
index=main host="security-log-source"| timechart count


### What This Establishes
- Confirms no epoch or future timestamp issues
- Shows event clustering based on log generation behavior
- Validates timestamp consistency

### Evidence
- Screenshot showing time bucket with event count
<img width="1942" height="665" alt="count3" src="https://github.com/user-attachments/assets/0935207a-9118-4d37-a7e4-6769fa2a5e72" />


---

## Command 4 – Field Extraction & SPL Usability Check (User Level)

### SPL Used
index=main host="security-log-source" | stats count by username auth_success


### What This Establishes
- Confirms `username` and `auth_success` fields are extracted
- Validates structured authentication data
- Confirms data usability for security analysis

### Evidence
- Screenshot showing per-user success and failure counts
<img width="1907" height="932" alt="4" src="https://github.com/user-attachments/assets/cf06baa6-7b1a-401d-8374-7eeb280188ad" />


---

## Command 5 – Source IP and Event Classification Validation

### SPL Used
index=main host="security-log-source"
| stats count by id.orig_h


### What This Establishes
This search confirms that source IP addresses are correctly extracted and allows counting authentication events per IP,
enabling identification of hosts generating high login activity and supporting IP-based security analysis.

### Evidence
- Screenshots showing IP-wise counts and event type distribution
<img width="1903" height="906" alt="5" src="https://github.com/user-attachments/assets/78d7744d-c2fe-4884-838f-2a80ddfe1a45" />


## Command 6 – Event Type Classification Validation

### SPL Used
index=main host="security-log-source"
| stats count by event_type

### What This Establishes
This search confirms that events are correctly classified by type and that the `event_type` field is properly extracted. It demonstrates that different categories of security events are identifiable, enabling structured analysis and supporting event-based detection logic in SOC environments.

### Evidence
- Screenshot showing event-type-wise count distribution
<img width="1915" height="473" alt="6" src="https://github.com/user-attachments/assets/80d0ba5f-b92d-4b42-ae8c-831e2b3f5418" />

---

## Outcome
This phase confirms that the security logs are correctly indexed, parsed using an appropriate sourcetype, and accurately timestamped. The data is verified to be reliable and analysis-ready, forming a solid foundation for detection logic and SOC-style security analysis in subsequent phases.
