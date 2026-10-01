# Indicators of Compromise (IOCs)

## Email Indicators

| Type | Indicator | Recommended Action |
|---|---|---|
| Sender address | security-alert@micros0ft-support.example | Block or quarantine |
| Reply-To address | verify-account@secure-login-alert.example | Block or quarantine |
| Sender domain | micros0ft-support.example | Block and search historical email logs |
| Reply-To domain | secure-login-alert.example | Block and search historical email logs |
| Display name | Microsoft 365 Security | Monitor for impersonation attempts |
| Subject | Action Required: Your Microsoft 365 account will be suspended | Search for similar messages |
| Message ID domain | micros0ft-support.example | Search email gateway logs |
| Source IP | 203.0.113.50 | Review reputation and search email/security logs |

## URL Indicator

| Type | Indicator | Recommended Action |
|---|---|---|
| URL | hxxps://microsoft-account-verify.example/login | Block at secure email gateway, DNS filter, proxy, and firewall |
| Domain | microsoft-account-verify.example | Block and search proxy/DNS logs |

## Threat-Hunting Queries

- Search for emails sent from `micros0ft-support.example`
- Search for messages with the subject: `Action Required: Your Microsoft 365 account will be suspended`
- Search for clicks or DNS requests involving `microsoft-account-verify.example`
- Review Microsoft 365 sign-in activity for users who received the email
- Look for new inbox rules, MFA changes, unfamiliar sign-in locations, or unusual OAuth consent activity

## Notes
All indicators in this project are simulated and use `.example` domains and documentation-range IP addresses. They are safe training data only and should not be treated as real malicious infrastructure.
