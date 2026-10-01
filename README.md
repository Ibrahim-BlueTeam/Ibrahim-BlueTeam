## Hi there 👋

# Ibrahim Causevic | SOC Analyst Detection Portfolio

Welcome to my cybersecurity portfolio.

I am a certified SOC Analyst with hands-on experience in security monitoring, alert triage, incident investigation, threat detection, and 24/7 security operations. This repository demonstrates practical SOC detection and investigation projects using simulated and sanitized security data.

My goal is to build and improve detection use cases, investigate suspicious activity, map findings to the MITRE ATT&CK framework, document indicators of compromise (IOCs), and produce clear incident reports.

## About Me

I am a cybersecurity professional focused on Security Operations Center (SOC), incident response, threat detection, and cloud/endpoint security.

My experience includes monitoring security events, investigating alerts, analyzing endpoint, identity, network, and cloud telemetry, escalating confirmed threats, and documenting findings. I have worked with Splunk, Microsoft Sentinel, Microsoft Defender, CrowdStrike, SentinelOne, Azure, Elastic, and other security-monitoring technologies.

I am currently expanding my skills in Microsoft Sentinel, KQL, cloud security, detection engineering, and incident response.

## Certifications

- CompTIA CySA+
- CompTIA Security+
- Google Cybersecurity Certificate

## Technical Skills

### Security Operations
- Security monitoring and alert triage
- Incident investigation and escalation
- Threat detection and threat hunting
- IOC identification and documentation
- Phishing and credential-compromise investigation
- Detection tuning and false-positive reduction
- Incident reporting and stakeholder communication

### SIEM, EDR, and Security Tools
- Splunk
- Microsoft Sentinel
- Microsoft Defender
- CrowdStrike
- SentinelOne
- Elastic
- IDS/IPS
- Firewall, endpoint, identity, and cloud log analysis

### Frameworks 
- MITRE ATT&CK
- NIST Cybersecurity Framework
- ISO 27001

  

## Portfolio Projects

### Brute Force Detector

**Status:** Completed  
**Validation:** Manually validated using simulated Windows Event ID 4625 CSV logs.  
**Detection Logic:** Splunk SPL query included for future testing in a compatible Splunk environment.  

**Objective:** Developed and documented a detection use case for repeated failed Windows logon attempts. The project identifies 10 or more failed logons from the same IP address against the same account within 10 minutes.

**MITRE ATT&CK:** T1110 – Brute Force

**Project Deliverables:**

- Simulated Windows authentication logs
- Splunk SPL detection query
- Manual CSV validation: 11 failed logons against `j.smith` from `203.0.113.25`
- Investigation worksheet and IOC documentation
- False-positive considerations and response recommendations
- One-page incident report

[View the completed project](./03-brute-force-detector/)

### Suspicious Scheduled Task Detector

**Status:** Completed

**Objective:** Developed a detection and investigation use case for suspicious Windows scheduled-task creation using simulated Event ID 4698 logs. The project focuses on identifying potential persistence or execution activity involving encoded PowerShell, command interpreters, suspicious task names, and user-writable file paths.

**MITRE ATT&CK:** T1053.005 – Scheduled Task/Job: Scheduled Task

**Project Deliverables:**

- Simulated Windows Event ID 4698 scheduled-task logs
- Detection logic for suspicious task creation
- Investigation notes and IOC documentation
- False-positive analysis
- Incident-response recommendations
- One-page incident report

[View the completed project](./07-suspicious-scheduled-task-detector/)


### Phishing Email Analyzer

**Status:** Completed

**Objective:** Analyzed a simulated Microsoft 365 credential-harvesting email by reviewing email headers, SPF/DKIM/DMARC results, sender and reply-to domains, social-engineering indicators, and a suspicious URL.

**MITRE ATT&CK:** T1566 – Phishing; T1566.002 – Spearphishing Link; T1204.001 – Malicious Link

**Project Deliverables:**

- Simulated phishing email and headers
- Email header and authentication analysis
- Indicators of compromise (IOCs)
- Investigation notes and response actions
- Phishing incident report
- Containment and remediation recommendations

[View the completed project](./01-phishing-email-analyzer/)



