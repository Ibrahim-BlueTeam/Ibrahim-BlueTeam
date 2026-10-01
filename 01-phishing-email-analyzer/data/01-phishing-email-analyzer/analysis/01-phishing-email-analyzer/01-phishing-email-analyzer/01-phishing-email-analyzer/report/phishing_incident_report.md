# Phishing Incident Report

## Executive Summary
A simulated phishing email impersonating Microsoft 365 Security was reported by a user. The email used urgency and a suspicious verification link to attempt credential theft. Header analysis identified a lookalike sender domain, a mismatched reply-to domain, failed SPF and DMARC results, and no DKIM signature.

## Incident Classification

| Field | Details |
|---|---|
| Incident Type | Credential-harvesting phishing |
| Severity | Medium |
| Status | Confirmed phishing attempt |
| Delivery Method | Email |
| MITRE ATT&CK | T1566 – Phishing; T1566.002 – Spearphishing Link; T1204.001 – Malicious Link |
| Impact | No confirmed user interaction in this simulated scenario |

## Key Indicators

| Type | Indicator |
|---|---|
| Sender | security-alert@micros0ft-support.example |
| Reply-To | verify-account@secure-login-alert.example |
| Malicious Domain | micros0ft-support.example |
| Phishing URL | hxxps://microsoft-account-verify.example/login |
| Source IP | 203.0.113.50 |
| Subject | Action Required: Your Microsoft 365 account will be suspended |

## Analysis Summary
The email impersonated Microsoft 365 and attempted to create urgency by claiming the recipient’s account would be suspended. The sender used a lookalike domain containing `micros0ft` instead of `microsoft`. The reply-to address used a separate untrusted domain. Email authentication results showed SPF failure, no DKIM signature, and DMARC failure. The URL domain was not associated with Microsoft and was assessed as a potential credential-harvesting site.

## Actions Recommended
1. Quarantine or purge the message from all affected mailboxes.
2. Block the sender, reply-to domain, sending domain, URL, and source IP.
3. Search email gateway, DNS, proxy, and web-filter logs for related indicators.
4. Identify affected recipients and determine whether anyone clicked the link.
5. If credentials were submitted, reset passwords, revoke active sessions, review MFA methods, and investigate sign-in activity.
6. Notify affected users and reinforce phishing-reporting procedures.
7. Update email-filtering rules to detect similar lookalike domains and subject lines.

## Lessons Learned
- Sender display names are not reliable proof of identity.
- Header and authentication analysis should be combined with content and URL review.
- Prompt phishing reporting helps security teams contain threats before users interact with malicious links.
- Security-awareness training should emphasize checking sender domains and reporting suspicious messages.

## Final Assessment
This was a simulated, confirmed phishing attempt designed to obtain Microsoft 365 credentials. No compromise was identified in the scenario. The recommended actions would contain the threat, identify user interaction, and reduce the chance of repeat delivery.

## Disclaimer
All email addresses, domains, IP addresses, URLs, and events in this project are simulated. This project is for defensive cybersecurity portfolio and training purposes only.
