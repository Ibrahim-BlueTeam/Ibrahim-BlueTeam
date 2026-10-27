# Indicators of Compromise (IOCs)

## URL Indicators

| Type | Indicator | Recommended Action |
|---|---|---|
| URL | hxxps://account-verification-secure.example/login | Block at secure email gateway, DNS filter, proxy, and firewall |
| Domain | account-verification-secure.example | Block and search email, DNS, proxy, and web-filter logs |
| Delivery Method | Simulated phishing email | Search mailboxes for related messages |
| Threat Type | Credential harvesting | Review sign-in activity for potentially affected users |

## File Indicators

| Type | Indicator | Recommended Action |
|---|---|---|
| SHA-256 | aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa | Block through EDR and antivirus controls |
| File Name | Invoice_2026.pdf.exe | Search endpoint and email telemetry |
| File Type | Windows PE executable | Investigate download and execution activity |
| Threat Type | Suspected malware | Isolate affected endpoints if execution is confirmed |

## Threat-Hunting Actions

- Search email logs for `account-verification-secure.example`.
- Search DNS, proxy, and web-filter logs for connections to the domain.
- Search EDR or antivirus telemetry for the SHA-256 hash.
- Search endpoints for the filename `Invoice_2026.pdf.exe`.
- Review process-execution telemetry for the file name, hash, and parent process.
- Review affected user accounts for unusual sign-ins, MFA changes, mailbox rules, or OAuth-consent changes.

## Notes

All indicators are simulated and use a `.example` domain and placeholder SHA-256 hash. They are safe training data only and must not be treated as real malicious infrastructure.
