# Phishing Investigation Notes

## Alert Details

| Field | Value |
|---|---|
| Incident Type | Suspected credential-harvesting phishing |
| Severity | Medium |
| Status | Confirmed phishing attempt |
| Reported By | Simulated employee |
| Primary Target | Microsoft 365 user accounts |
| Initial Access Technique | T1566.002 – Spearphishing Link |

## Evidence Reviewed
- Simulated phishing email and full headers
- Sender and reply-to domains
- SPF, DKIM, and DMARC results
- Embedded URL
- Email subject and social-engineering language

## Key Findings
- The display name impersonates Microsoft 365 Security.
- The sender domain uses a lookalike spelling: `micros0ft-support.example`.
- The reply-to domain does not match the sender domain.
- SPF failed, DKIM was not present, and DMARC failed.
- The email used urgency and threatened account suspension.
- The embedded URL does not belong to Microsoft and could be used for credential harvesting.
- No evidence exists in this simulated scenario that the recipient clicked the link or entered credentials.

## Scope and Validation Actions
1. Search the email gateway for the sender, reply-to address, subject line, and URL.
2. Identify all recipients and determine whether the message was delivered, quarantined, or reported.
3. Review proxy, DNS, and secure web gateway logs for requests to `microsoft-account-verify.example`.
4. Review Microsoft 365 or Entra ID sign-in logs for unusual sign-ins, impossible travel, unfamiliar devices, MFA changes, and failed or successful authentication attempts.
5. Review mailbox rules, forwarding settings, OAuth application consent, and recent account changes for impacted users.
6. Contact users who received or clicked the message to determine whether credentials or MFA prompts were approved.

## Recommended Containment Actions
- Purge or quarantine the phishing email from all affected mailboxes.
- Block the sender, reply-to address, domains, source IP, and malicious URL.
- Notify recipients not to click the link or provide credentials.
- If credentials were submitted, reset the password, revoke active sessions, review MFA methods, and investigate the account for unauthorized activity.
- Isolate and investigate any endpoint where a malicious attachment or download is confirmed.

## False-Positive Considerations
- A legitimate vendor may use a separate reply-to domain, but the lookalike domain, authentication failures, urgency, and suspicious URL make this message highly suspicious.
- SPF or DMARC failures alone do not prove phishing; the full set of indicators must be evaluated.

## Final Assessment
The email is a confirmed phishing attempt designed to capture Microsoft 365 credentials. In a real environment, the incident should remain open until email delivery, user interaction, sign-in activity, and mailbox/account changes have been reviewed.
