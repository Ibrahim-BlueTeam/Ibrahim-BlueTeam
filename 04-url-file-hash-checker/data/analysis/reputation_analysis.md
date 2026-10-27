# URL and File Hash Reputation Analysis

## Investigation Summary
A simulated phishing alert contained a suspicious URL, and a simulated endpoint alert identified a suspicious Windows executable. Both indicators were reviewed using simulated VirusTotal-style reputation results and surrounding alert context.

## URL Analysis

| Field | Finding |
|---|---|
| URL | hxxps://account-verification-secure.example/login |
| Delivery Method | Simulated phishing email |
| Primary Risk | Credential harvesting |
| Vendor Results | 18 malicious, 4 suspicious |
| Triage Verdict | Malicious |
| Confidence | High |

### URL Assessment
The URL appears to imitate an account-verification page and was delivered through a simulated phishing email. Multiple simulated security vendors classified it as malicious or suspicious. The domain does not match the legitimate organization it claims to represent.

### Recommended URL Actions
- Block the URL and domain in the secure email gateway, DNS filter, proxy, and firewall.
- Search email logs for messages containing the URL or domain.
- Search DNS, proxy, and web-filter logs for user visits or clicks.
- Identify affected users and review their sign-in activity.
- Reset credentials and revoke sessions if a user entered credentials.

## File Hash Analysis

| Field | Finding |
|---|---|
| File Name | Invoice_2026.pdf.exe |
| File Type | Windows PE executable |
| SHA-256 | aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa |
| Vendor Results | 42 malicious, 3 suspicious |
| Triage Verdict | Malicious |
| Confidence | High |

### File Assessment
The file uses a double extension intended to appear as a PDF document while actually being a Windows executable. The high number of simulated malicious detections and the phishing context support a malicious classification.

### Recommended File Actions
- Isolate affected endpoints if the file was downloaded or executed.
- Block the SHA-256 hash through EDR and antivirus controls.
- Search EDR and SIEM telemetry for the file hash, filename, parent process, and execution events.
- Collect relevant endpoint evidence and investigate possible persistence or credential theft.
- Remove the file and confirm that no related malicious activity remains.

## MITRE ATT&CK Mapping

| Technique | Description |
|---|---|
| T1566.002 | Phishing: Spearphishing Link |
| T1204.001 | User Execution: Malicious Link |
| T1204.002 | User Execution: Malicious File |

## Final Verdict
Both simulated indicators are classified as **Malicious** with high confidence. The URL should be blocked and investigated for user interaction. The file hash should be blocked, scoped across endpoints, and investigated for execution and related activity.

## Disclaimer
All indicators, detections, and findings in this project are simulated for defensive training and portfolio purposes only.
