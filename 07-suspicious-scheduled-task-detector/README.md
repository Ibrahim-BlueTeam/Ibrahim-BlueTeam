# Suspicious Scheduled Task Detector

**Status:** In Progress  
**Project Type:** Windows Persistence Detection Use Case  
**Data Source:** Simulated Windows Security Event Logs  
**Primary Event ID:** 4698 — A scheduled task was created  

## Objective

Develop a detection and investigation use case for potentially suspicious Windows scheduled tasks that may be used for persistence, execution, or privilege escalation.

This project uses simulated Windows Event ID 4698 logs and GitHub documentation. The included Splunk SPL query is implementation logic and was not tested in a local Splunk environment.

## Threat Scenario

Attackers may create scheduled tasks to run malicious programs or scripts at system startup, user logon, or recurring intervals. This technique can help an attacker maintain persistence after initial access.

The simulated scenario includes a suspicious task created under the Task Scheduler Library root directory. The task runs PowerShell with an encoded command from a user-writable directory.

## MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---|---|---|
| Execution | Scheduled Task/Job: Scheduled Task | T1053.005 |
| Persistence | Scheduled Task/Job: Scheduled Task | T1053.005 |
| Privilege Escalation | Scheduled Task/Job: Scheduled Task | T1053.005 |
| Command and Scripting Interpreter: PowerShell | PowerShell | T1059.001 |

## Detection Logic

Alert when Windows Security Event ID 4698 shows newly created scheduled tasks with one or more suspicious indicators:

- A task created in the Task Scheduler Library root directory
- PowerShell, cmd.exe, wscript.exe, cscript.exe, mshta.exe, rundll32.exe, or regsvr32.exe execution
- Encoded PowerShell commands
- Executables or scripts launched from user-writable paths such as AppData, Temp, Downloads, or Public
- Unusual task names designed to look legitimate
- Tasks created by unexpected user accounts or outside approved maintenance windows

## Planned Deliverables

- Simulated Windows Event ID 4698 CSV logs
- Detection logic and Splunk SPL query
- Alert investigation worksheet
- IOC list
- False-positive analysis
- Incident-response recommendations
- One-page incident report

## Skills Demonstrated

- Windows Security Event Log analysis
- Detection engineering
- SIEM/Splunk SPL logic
- Persistence investigation
- MITRE ATT&CK mapping
- Alert triage and incident response
- Technical documentation

## Disclaimer

All data in this repository is simulated for educational and portfolio purposes. No malware, credentials, or real organizational data is included.
