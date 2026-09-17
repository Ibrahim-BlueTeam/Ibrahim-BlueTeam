# Brute Force Investigation Worksheet

## Alert Information

| Field | Value |
|---|---|
| Detection name | Repeated Failed Windows Logons |
| Severity | Medium |
| Status | Closed – Simulated True Positive |
| MITRE ATT&CK | T1110 – Brute Force |

## Evidence

| Field | Value |
|---|---|
| Windows Event ID | 4625 |
| Target user | j.smith |
| Source IP | 203.0.113.25 |
| Host | DC01 |
| Workstation | WKSTN-22 |
| Logon type | 3 – Network |
| Failed attempts | 11 |
| Time range | 09:00:05–09:06:22 UTC |
| Failure reason | Unknown user name or bad password |

## IOCs

- Source IP: `203.0.113.25`
- Target user: `j.smith`
- Host: `DC01`
- Workstation: `WKSTN-22`
- Windows Event ID: `4625`

## Investigation Questions

- Is the source IP authorized or associated with a VPN, vendor, or business partner?
- Is `j.smith` an active user account?
- Did a successful Windows Event ID 4624 login occur after these failures?
- Did the source IP target other users or computers?
- Could a user entering an incorrect password, stale credentials, or a service account explain the activity?
- Is MFA enabled for the affected account?

## Analysis

The IP address `203.0.113.25` generated 11 failed network logon attempts against `j.smith` on `DC01` in approximately six minutes. The activity exceeded the configured threshold of 10 failed attempts within 10 minutes.

The event pattern was classified as a simulated true positive for suspicious brute-force activity. The simulated dataset does not contain a successful logon event.

## Recommended Actions

- Validate whether the source IP is authorized.
- Search for Event ID 4624 successful logons for the same user and source IP.
- Investigate whether additional accounts or hosts were targeted.
- Block or restrict the source IP if it is unauthorized.
- Reset the affected account password if compromise is suspected.
- Confirm MFA and conditional-access protections are active.
