# URL and File Hash Checker

## Objective
Perform manual threat-intelligence enrichment for suspicious URLs and file hashes using simulated VirusTotal-style results. Analyze the evidence, assign a SOC triage verdict, document indicators of compromise, and recommend response actions.

## Scenario
A SOC analyst receives an alert involving a suspicious URL sent through email and a file hash detected on an endpoint. The objective is to determine whether the indicators are malicious, suspicious, or require additional investigation.

## Analysis Scope
- Review URL reputation results
- Review SHA-256 file hash reputation results
- Compare malicious, suspicious, harmless, and undetected vendor results
- Document IOCs
- Assign a triage verdict
- Map findings to MITRE ATT&CK
- Recommend containment and investigation actions

## Tools and Methods
- Simulated VirusTotal-style reputation results
- Manual IOC analysis
- Threat-intelligence enrichment workflow
- GitHub documentation and incident reporting

## Planned Deliverables
- Simulated URL and file-hash reputation results
- URL analysis
- File-hash analysis
- IOC list
- Investigation notes
- Incident report
- Containment recommendations

## MITRE ATT&CK Mapping
- T1566.002: Phishing: Spearphishing Link
- T1204.001: User Execution: Malicious Link
- T1204.002: User Execution: Malicious File

## Disclaimer
This is a defensive cybersecurity portfolio project using simulated data only. No malicious URL was visited, no file was downloaded or executed, and no VirusTotal API key was used or stored in this repository.
