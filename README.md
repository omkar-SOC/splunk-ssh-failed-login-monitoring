# SSH Failed Login Monitoring using Splunk

## Project Overview
This project demonstrates SOC-style log analysis using Splunk Enterprise to detect failed SSH login attempts and suspicious attacker activity from Linux authentication logs.

---

## Tools Used
- Splunk Enterprise
- Linux auth.log
- SPL (Search Processing Language)

---

## Objectives
- Analyze failed SSH login attempts
- Identify suspicious attacker IP addresses
- Detect possible brute-force activity
- Visualize authentication attack trends

---

## SPL Queries Used

### Failed Login Detection
```spl
index=* "failed password"
```

### Attacker IP Extraction and Analysis
```spl
index=* "failed password"
| rex "from (?<attacker_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by attacker_ip
| sort - count
```

### Failed Login Trend Analysis
```spl
index=* "failed password"
| timechart count
```

---

## Dashboard Created
SSH Failed Login Monitoring Dashboard

Dashboard Panels:
- Failed Login Trend Analysis
- Top Attacking IP Addresses
- Authentication Activity Monitoring

---

## Key Findings
- Identified attacker IPs generating high failed login attempts
- Observed suspicious SSH authentication behavior
- Detected possible brute-force attack activity
- Visualized login attack patterns over time

---

## Practical Concepts Learned
- Log ingestion in Splunk
- SPL querying and filtering
- Regex extraction using rex
- Dashboard creation and visualization
- Authentication log analysis
- Time-range filtering
- Event statistics and trend monitoring

---

## Additional Learning
While practicing, duplicate logs were accidentally uploaded multiple times, which increased event counts.

From this, I learned the importance of:
- creating dedicated indexes for projects
- selecting the correct index during log ingestion
- maintaining clean and organized SIEM environments

Using separate indexes for each project helps avoid duplicate log confusion and keeps analysis cleaner during practice and monitoring.

---

## Screenshots

Screenshots are available in the `screenshots` folder.

---

## Queries

All SPL queries used in this project are available in the `queries` folder.
