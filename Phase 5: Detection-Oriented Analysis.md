## Detection Use Case 1 – Brute-Force Login Behavior (SSH)

### Detection Logic

A high volume of SSH connection attempts from multiple external hosts toward SSH services may indicate brute-force or password spraying activity.

# SPL Used
index=main id.resp_p=22 | stats count AS ssh_attempts

# What This Detection Establishes

Confirms overall SSH attack surface exposure and validates whether SSH services are actively being targeted at the network level.

<img width="1917" height="543" alt="5 1" src="https://github.com/user-attachments/assets/f9abc156-c0e8-43cb-81f0-8e78d47aa116" />




## Detection Use Case 2 – Excessive SSH Attempts from a Single Source IP
### Detection Logic

A single source IP repeatedly attempting SSH connections is a strong indicator of brute-force automation.

# SPL Used
index=main id.resp_p=22 | stats count AS attempts BY id.orig_h | sort - attempts
# What This Detection Establishes

Identifies high-volume source IPs exhibiting abnormal SSH connection behavior that may warrant blocking or further investigation.
<img width="1918" height="928" alt="5 2" src="https://github.com/user-attachments/assets/164c33e6-96d0-49d5-acda-70bab05fac24" />



## Detection Use Case 3 – One Source Targeting Multiple SSH Servers
### Detection Logic

Attackers often scan or brute-force multiple servers from the same source to increase success probability.

# SPL Used
index=main id.resp_p=22 | stats dc(id.resp_h) AS targeted_hosts BY id.orig_h | sort - targeted_hosts

# What This Detection Establishes
Highlights lateral targeting behavior, where a single source IP probes or attacks multiple SSH endpoints.
<img width="1913" height="942" alt="5 3" src="https://github.com/user-attachments/assets/50af387f-030b-423a-8003-a39dd2b8569a" />



## Detection Use Case 4 – High-Risk SSH Activity Classification
### Detection Logic

SOC analysts often categorize activity based on risk level to prioritize investigations.

# SPL Used
index=main
id.resp_p=22
| eval risk_level=case(
    count>100,"High",
    count>50,"Medium",
    true(),"Low"
)
| stats count BY risk_level

# What This Detection Establishes
Demonstrates risk-based thinking, showing how raw network activity can be translated into actionable severity levels.
<img width="1918" height="552" alt="5 4" src="https://github.com/user-attachments/assets/ed66bb8d-43cb-4a6c-8deb-d37f190ce6f0" />


## Detection Use Case 5 - Identify the top SSH attacker

### Detection Logic

This query measures the total volume of SSH connection attempts at the network layer. 
The result represents overall SSH exposure and serves as a baseline for detecting abnormal spikes or concentrated attack behaviour.

# SPL Used

index=main
id.resp_p=22
| stats count BY id.orig_h
| sort - count
| head 1

<img width="1918" height="518" alt="5 5" src="https://github.com/user-attachments/assets/98eb6bb2-3ce0-4c91-8de0-4a97fdd7b0b4" />
