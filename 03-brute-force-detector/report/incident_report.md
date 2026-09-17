# Incident Report: Suspected Brute-Force Activity

**Date:** September 17, 2026  
**Severity:** Medium  
**Status:** Closed – Simulated True Positive  
**MITRE ATT&CK:** T1110 – Brute Force  

## Executive Summary

Security monitoring identified repeated failed Windows login attempts against account `j.smith` on host `DC01`. The activity came from source IP address `203.0.113.25` and produced 11 Windows Security Event ID 4625 events in approximately six minutes.

The activity exceeded the detection threshold of 10 failed logons within 10 minutes and was classified as suspicious brute-force behavior. The simulated data did not contain a successful login event.

## Scope

| Item | Value |
|---|---|
| Target account | j.smith |
| Target host | DC01 |
| Source IP | 203.0.113.25 |
| Failed attempts | 11 |
| Successful login observed | No |
| Impact | No confirmed unauthorized access |

## Indicators of Compromise

- Source IP: `203.0.113.25`
- Target account: `j.smith`
- Target host: `DC01`
- Workstation: `WKSTN-22`
- Windows Event ID: `4625`

## Analysis

The same source IP repeatedly attempted a network login to the same user account within a short time period. This behavior is consistent with a possible brute-force attempt and maps to MITRE ATT&CK technique T1110.

No successful Event ID 4624 logon was included in the simulated dataset. Therefore, the available evidence does not confirm account compromise or unauthorized access.

## Recommended Actions

- Confirm whether source IP `203.0.113.25` is authorized.
- Search for Event ID 4624 successful logons associated with the same IP address and account.
- Investigate whether the source IP targeted additional accounts or systems.
- Block the IP address if it is unauthorized.
- Reset the account password if compromise is suspected.
- Confirm MFA and conditional-access controls are enabled.
- Tune the detection threshold only after reviewing normal authentication activity.
