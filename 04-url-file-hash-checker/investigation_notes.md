# URL and File Hash Investigation Notes

## Alert Details

| Field | Value |
|---|---|
| Incident Type | Suspected phishing and malware delivery |
| Severity | High |
| Status | Confirmed malicious indicators |
| Alert Sources | Simulated email alert and endpoint alert |
| URL Verdict | Malicious |
| File Hash Verdict | Malicious |

## Evidence Reviewed
- Simulated URL reputation results
- Simulated SHA-256 file-hash reputation results
- Phishing-email delivery context
- File name and file type
- Simulated security-vendor detection counts

## Key Findings
- The URL resembles an account-verification site and may be used for credential harvesting.
- The URL was classified as malicious by 18 simulated security vendors and suspicious by 4 vendors.
- The file name `Invoice_2026.pdf.exe` uses a double extension to appear as a PDF document.
- The file is a Windows executable, not a PDF document.
- The SHA-256 file hash was classified as malicious by 42 simulated security vendors.
- No live malicious URL was opened, and no file was downloaded or executed for this portfolio project.

## Scope and Validation Actions
1. Search email-security logs for messages containing the URL or domain.
2. Identify users who received the phishing message.
3. Search DNS, proxy, and web-filter logs for requests to `account-verification-secure.example`.
4. Search EDR, antivirus, and SIEM telemetry for the SHA-256 hash and filename.
5. Review endpoint process-execution events for `Invoice_2026.pdf.exe`.
6. Identify endpoints where the file was downloaded, created, executed, or quarantined.
7. Review affected user accounts for unusual sign-ins, MFA changes, mailbox rules, and OAuth-consent changes.

## Containment Actions
- Block the malicious URL and domain through email, DNS, proxy, and firewall controls.
- Purge the phishing email from affected mailboxes.
- Block the SHA-256 hash using EDR and antivirus controls.
- Isolate any endpoint where file execution is confirmed.
- Reset passwords and revoke active sessions if users submitted credentials.
- Preserve relevant email, endpoint, proxy, DNS, and authentication logs.

## MITRE ATT&CK Mapping
- T1566.002: Phishing: Spearphishing Link
- T1204.001: User Execution: Malicious Link
- T1204.002: User Execution: Malicious File

## Final Assessment
The simulated URL and file hash are confirmed malicious indicators. The incident should remain open until the security team confirms that the URL was blocked, affected mailboxes were remediated, endpoint execution was scoped, and any potentially compromised accounts were secured.

## Disclaimer
All indicators, findings, and actions are simulated for defensive training and portfolio purposes only.
