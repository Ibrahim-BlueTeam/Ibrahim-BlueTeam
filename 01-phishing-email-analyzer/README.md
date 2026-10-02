# Phishing Email Analyzer

## Objective
Analyze a simulated suspicious email to identify phishing indicators, review email authentication results, document IOCs, map activity to MITRE ATT&CK, and recommend response actions.

## Scenario
A user reported an email that appeared to be from Microsoft 365 support. The email urged the recipient to click a link to prevent their account from being suspended.

## Analysis Scope
- Review sender and reply-to addresses
- Review email headers and authentication results
- Analyze SPF, DKIM, and DMARC
- Identify suspicious URLs and social-engineering indicators
- Document IOCs
- Map the activity to MITRE ATT&CK
- Provide incident-response recommendations

## MITRE ATT&CK Mapping
- T1566: Phishing
- T1566.002: Spearphishing Link
- T1204.001: User Execution: Malicious Link

## Planned Deliverables
- Simulated phishing email and headers
- Email-header analysis
- IOC list
- Investigation notes
- Incident report
- Response recommendations

- ## Skills Demonstrated

- Phishing email triage
- Email header analysis
- Indicator of compromise extraction
- Threat intelligence enrichment
- MITRE ATT&CK mapping
- Incident-response recommendations
- Security investigation documentation

- ## Recommended Response Actions

1. Quarantine and remove the phishing email from affected mailboxes.
2. Block the malicious sender address, domain, URL, and related IP addresses.
3. Search email, proxy, DNS, and endpoint logs for IOC matches and user clicks.
4. Reset passwords and revoke active sessions for any user who submitted credentials.
5. Review Microsoft 365 or identity-provider sign-in logs for suspicious activity.
6. Enforce MFA and notify users of the phishing campaign.

## MITRE ATT&CK Mapping

| Tactic | Technique | ID | Evidence |
|---|---|---|---|
| Initial Access | Phishing: Spearphishing Link | T1566.002 | The email uses a link to direct the recipient to a suspected credential-harvesting site. |
| Credential Access / Initial Access | Valid Accounts | T1078 | If credentials are harvested, an attacker may attempt to authenticate using the victim's legitimate account. |


- ## Project Files

- [Email header analysis](analysis/header_analysis.md)
- [Indicators of compromise (IOCs)](analysis/iocs.md)
- [Simulated phishing email sample](data/simulated_phishing_email.txt)


## Disclaimer
This is a defensive cybersecurity portfolio project that uses simulated data only. No malicious links were accessed, opened, or executed.
