# URL and File Hash Incident Report

## Executive Summary
A simulated security investigation identified a malicious URL delivered through phishing and a malicious Windows executable detected on an endpoint. Simulated reputation results showed multiple security-vendor detections for both indicators. The URL was assessed as a credential-harvesting attempt, and the file was assessed as potential malware delivered through social engineering.

## Incident Classification

| Field | Details |
|---|---|
| Incident Type | Phishing and suspected malware delivery |
| Severity | High |
| Status | Confirmed malicious indicators |
| URL Verdict | Malicious |
| File Hash Verdict | Malicious |
| Impact | No confirmed execution or credential compromise in this simulated scenario |

## Key Indicators

| Type | Indicator |
|---|---|
| URL | hxxps://account-verification-secure.example/login |
| Domain | account-verification-secure.example |
| SHA-256 | aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa |
| File Name | Invoice_2026.pdf.exe |
| File Type | Windows PE executable |

## Analysis Summary
The URL was delivered through a simulated phishing email and used an account-verification theme associated with credential harvesting. Simulated vendor results included 18 malicious and 4 suspicious classifications.

The file used a double extension, `Invoice_2026.pdf.exe`, to appear as a PDF while actually being a Windows executable. Simulated vendor results included 42 malicious and 3 suspicious classifications. The URL and file were both classified as malicious with high confidence.

## MITRE ATT&CK Mapping

| Technique | Description |
|---|---|
| T1566.002 | Phishing: Spearphishing Link |
| T1204.001 | User Execution: Malicious Link |
| T1204.002 | User Execution: Malicious File |

## Recommended Response Actions
1. Block the URL and domain using email, DNS, proxy, and firewall security controls.
2. Purge phishing messages containing the URL from affected mailboxes.
3. Search email, DNS, proxy, and web-filter logs for user interaction with the domain.
4. Block the SHA-256 hash using EDR and antivirus controls.
5. Search endpoint and SIEM telemetry for the hash, filename, file creation, download, and execution events.
6. Isolate endpoints if the suspicious executable was executed.
7. Reset passwords, revoke sessions, and review MFA methods if users submitted credentials.
8. Preserve relevant email, network, endpoint, and authentication logs for follow-up investigation.

## Lessons Learned
- Threat-intelligence results should be assessed together with delivery context, file type, and endpoint activity.
- A double file extension can be used to disguise a Windows executable as a document.
- A suspicious URL should be blocked and investigated for user interaction, even if endpoint execution is not confirmed.
- Documenting IOCs and response actions supports faster containment and consistent incident handling.

## Final Assessment
The simulated URL and file hash were confirmed malicious. Recommended actions focus on blocking the indicators, identifying exposure, investigating endpoint activity, and protecting any potentially affected user accounts.

## Disclaimer
All indicators, reputation results, findings, and response actions in this project are simulated for defensive cybersecurity training and portfolio purposes only.
