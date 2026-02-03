## Exploratory Security Log Analysis using SPL

This phase focuses on transforming raw authentication logs into actionable security insights using Search Processing Language (SPL). The goal is to simulate real-world SOC investigations by identifying abnormal login behaviour, attack patterns, and authentication trends.

## Command 1 – Successful SSH Login Count

### SPL Used
index=main host="security-log-source" event_type="Successful SSH Login" | stats count AS successful_logins


# What This Establishes

This query calculates the total number of successful SSH authentications observed in the dataset.
It helps establish a baseline of legitimate access activity, which is critical for comparing against failed authentication attempts and identifying anomalies.

# Observed Outcome

Successful SSH Login events: 612
<img width="1917" height="482" alt="4 1" src="https://github.com/user-attachments/assets/76203083-16c0-478e-b3d4-72afa5b7df49" />


## Command 2 – Failed SSH Login Count 

### SPL Used
index=main host="security-log-source" event_type="Failed SSH Login" | stats count AS failed_logins

# What This Establishes

This command identifies the total number of failed SSH authentication attempts, which is a primary indicator of brute-force attacks, credential guessing, or unauthorized access attempts.

# Observed Outcome

Failed SSH Login events: 610
<img width="1918" height="693" alt="4 2" src="https://github.com/user-attachments/assets/14e1eb25-cdc3-4129-8208-b76d50f3fe24" />


## Command 3 - Authentication Event Distribution

### SPL Used
index=main host="security-log-source" | stats count BY event_type

# What This Establishes

This query provides a high-level breakdown of all authentication-related event types present in the dataset.
It allows analysts to quickly understand the security posture and dominant authentication behaviors within the environment.

# Observed Outcome
Event Type	Count
Successful SSH Login	612
Failed SSH Login	610
Multiple Failed Authentication Attempts	606
Connection Without Authentication	572
<img width="1918" height="515" alt="4 3" src="https://github.com/user-attachments/assets/3283126a-115f-49f8-a607-00cde19bec88" />


## Command 4 - Authentication Activity Over Time

### SPL Used

index=main host="security-log-source" | timechart span=1h count AS auth_events

## What This Establishes

This query visualises authentication activity trends over time, enabling detection of:

-> Sudden spikes in login attempts
-> Time-based attack patterns
-> Off-hours authentication anomalies

# Observed Outcome

Total authentication events visualized over time: 2400

<img width="1918" height="570" alt="4 5" src="https://github.com/user-attachments/assets/8c0ca043-2a81-4773-a63d-864222457736" />

