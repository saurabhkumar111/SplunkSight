## Exploratory Security Log Analysis using SPL

This phase focuses on transforming raw authentication logs into actionable security insights using Search Processing Language (SPL). The goal is to simulate real-world SOC investigations by identifying abnormal login behaviour, attack patterns, and authentication trends.

## Command 1 – Successful Login Count

### SPL Used
index=main sourcetype=linux_secure action=success| stats count AS successful_logins
