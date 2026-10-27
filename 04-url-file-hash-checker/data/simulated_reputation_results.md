# Simulated URL and File Hash Reputation Results

## Disclaimer
All indicators and reputation results in this file are simulated for defensive training purposes. No live URL was visited, no file was uploaded, and no VirusTotal API key was used.

---

## Indicator 1: Suspicious URL

| Field | Value |
|---|---|
| Indicator Type | URL |
| URL | hxxps://account-verification-secure.example/login |
| Source | Simulated phishing-email alert |
| URL Category | Phishing / Credential Harvesting |
| Final Verdict | Malicious |
| Confidence | High |

### Simulated Reputation Summary

| Result | Vendor Count |
|---|---:|
| Malicious | 18 |
| Suspicious | 4 |
| Harmless | 0 |
| Undetected | 72 |
| Timeout | 1 |

### Observed Risk Indicators
- Lookalike account-verification domain
- Login page designed to collect credentials
- URL delivered through a simulated phishing email
- Multiple security vendors classified the URL as malicious or suspicious
- URL is not associated with the legitimate organization it impersonates

### SOC Triage Decision
**Malicious.** Block the URL and domain. Search email, DNS, proxy, and web-filter logs for user interaction.

---

## Indicator 2: Suspicious File Hash

| Field | Value |
|---|---|
| Indicator Type | SHA-256 File Hash |
| SHA-256 | `aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa` |
| File Name | `Invoice_2026.pdf.exe` |
| File Type | Windows PE executable |
| Source | Simulated endpoint alert |
| Final Verdict | Malicious |
| Confidence | High |

### Simulated Reputation Summary

| Result | Vendor Count |
|---|---:|
| Malicious | 42 |
| Suspicious | 3 |
| Harmless | 0 |
| Undetected | 21 |
| Timeout | 0 |

### Observed Risk Indicators
- Double-extension filename intended to appear as a PDF
- Executable file type rather than a document
- High number of malicious vendor classifications
- File originated from a simulated phishing investigation

### SOC Triage Decision
**Malicious.** Isolate affected endpoints, block the hash in EDR or antivirus controls, identify all devices with the hash, and investigate execution activity.

---

## Analyst Notes
A low or zero detection count does not automatically mean an indicator is safe. The analyst should also consider the source of the alert, file type, email context, domain reputation, endpoint activity, and business impact before closing an investigation.
