# Incident Report: Suspicious Scheduled Task Activity

**Incident ID:** IR-2026-001  
**Date Identified:** 2026-09-20  
**Severity:** High  
**Status:** Closed — Simulated Investigation  
**Analyst:** Ibrahim Causevic  

## Executive Summary

A simulated security investigation identified multiple suspicious scheduled tasks created on `FIN-WS-03` by `ACME\jsmith`. The tasks used deceptive names that imitated Windows or Microsoft software and executed commands from user-writable directories.

The highest-risk task, `\MicrosoftEdgeUpdate`, launched hidden PowerShell with an encoded command that attempted to download content from external IP address `185.220.101.45`. This activity is consistent with potential persistence and command execution through Windows Task Scheduler.

## Scope and Impact

| Category | Finding |
|---|---|
| Affected host | `FIN-WS-03` |
| Affected account | `ACME\jsmith` |
| Detection source | Windows Security Event ID 4698 |
| Related MITRE technique | T1053.005 — Scheduled Task/Job: Scheduled Task |
| Potential impact | Persistence, unauthorized code execution, possible malware download, and account compromise |

## Key Evidence

| Time | Evidence |
|---|---|
| 10:42:09 | `\WindowsUpdateCheck` created to execute `C:\Users\jsmith\AppData\Roaming\update.exe` at user logon |
| 10:44:51 | `\MicrosoftEdgeUpdate` created to execute hidden PowerShell with an encoded command and external download behavior |
| 10:48:16 | `\SystemHealthMonitor` created to run `C:\Users\jsmith\Downloads\healthcheck.bat` every 30 minutes |
| 18:05:33 | `\WindowsTelemetry` created to run `C:\Users\jsmith\AppData\Local\Temp\telemetry.vbs` at user logon |

## Indicators of Compromise

- Host: `FIN-WS-03`
- User: `ACME\jsmith`
- External IP: `185.220.101.45`
- Task names: `\WindowsUpdateCheck`, `\MicrosoftEdgeUpdate`, `\SystemHealthMonitor`, `\WindowsTelemetry`
- Files: `update.exe`, `healthcheck.bat`, `telemetry.vbs`
- Processes: `powershell.exe`, `cmd.exe`, and `wscript.exe`

## Response Actions

1. Preserve relevant logs, scheduled-task details, and endpoint artifacts before making changes.
2. Isolate `FIN-WS-03` if the activity is confirmed as malicious or remains active.
3. Disable and remove malicious tasks after evidence preservation.
4. Quarantine suspicious files and perform endpoint analysis or EDR scanning.
5. Block the external IP after validating that it is malicious and not business-required.
6. Reset credentials and revoke sessions for `ACME\jsmith` if compromise is confirmed.
7. Hunt across endpoints for the same task names, file paths, commands, account, and IP address.

## Lessons Learned

- Scheduled-task creation should be centrally logged and monitored.
- Alerts should prioritize encoded PowerShell, hidden execution, user-writable execution paths, external download behavior, and deceptive task names.
- Maintain a baseline of approved scheduled tasks, update detection exclusions through a documented change-management process, and periodically validate the detection logic.

## Portfolio Disclaimer

This report is based entirely on simulated logs created for educational and portfolio purposes. The report demonstrates alert triage, evidence analysis, MITRE ATT&CK mapping, incident documentation, and recommended response actions.
