# Investigation Notes

## Alert Summary

**Alert Name:** Suspicious Scheduled Task Created  
**Detection Source:** Windows Security Event ID 4698  
**MITRE ATT&CK:** T1053.005 — Scheduled Task/Job: Scheduled Task  
**Severity:** High  

## Suspicious Activity Identified

The simulated log review identified multiple suspicious scheduled tasks. The highest-priority activity occurred on `FIN-WS-03` and was created by the account `ACME\jsmith`.

The scheduled task named `\MicrosoftEdgeUpdate` used PowerShell with hidden-window execution and an encoded command. The encoded command included a download action from the external IP address `185.220.101.45`.

## Related Events

| Time | Host | User | Task Name | Suspicious Indicator |
|---|---|---|---|---|
| 2026-09-20 10:42:09 | FIN-WS-03 | ACME\jsmith | \WindowsUpdateCheck | Executable launched from AppData |
| 2026-09-20 10:44:51 | FIN-WS-03 | ACME\jsmith | \MicrosoftEdgeUpdate | Encoded PowerShell and external download |
| 2026-09-20 10:48:16 | FIN-WS-03 | ACME\jsmith | \SystemHealthMonitor | Batch script launched from Downloads |
| 2026-09-20 18:05:33 | FIN-WS-03 | ACME\jsmith | \WindowsTelemetry | VBScript launched from Temp |

## Initial Assessment

The tasks were created by the same user account, on the same endpoint, and in a short time period. The scheduled-task names imitate legitimate Windows or Microsoft software, but their commands execute from user-writable directories or use obfuscated PowerShell.

This pattern is consistent with possible persistence and execution through Windows Task Scheduler.

## Indicators of Compromise

- Hostname: `FIN-WS-03`
- User account: `ACME\jsmith`
- Source IP address: `185.220.101.45`
- Suspicious task names: `\WindowsUpdateCheck`, `\MicrosoftEdgeUpdate`, `\SystemHealthMonitor`, `\WindowsTelemetry`
- Suspicious file paths:
  - `C:\Users\jsmith\AppData\Roaming\update.exe`
  - `C:\Users\jsmith\Downloads\healthcheck.bat`
  - `C:\Users\jsmith\AppData\Local\Temp\telemetry.vbs`
- Suspicious process execution:
  - `powershell.exe -NoProfile -WindowStyle Hidden -EncodedCommand`
  - `cmd.exe /c`
  - `wscript.exe`

## Investigation Steps

1. Validate whether `ACME\jsmith` was authorized to create the tasks.
2. Review Event ID 4624 activity using logon ID `0x1d77` to identify the associated logon session.
3. Review endpoint telemetry for execution of `update.exe`, `healthcheck.bat`, and `telemetry.vbs`.
4. Decode and analyze the PowerShell encoded command in a safe, isolated environment.
5. Search for network connections to `185.220.101.45` and identify any additional affected hosts.
6. Identify whether the task creator account shows signs of compromise, including unusual logons, mailbox activity, or authentication attempts.
7. Review other scheduled tasks created, modified, enabled, or deleted by the same account or on the same endpoint.

## Recommended Response Actions

1. Isolate `FIN-WS-03` from the network if malicious activity is confirmed or active.
2. Disable and remove the suspicious scheduled tasks after preserving evidence.
3. Quarantine the identified files and collect endpoint forensic evidence.
4. Block `185.220.101.45` at network security controls after validation.
5. Reset the password and revoke active sessions for `ACME\jsmith` if account compromise is suspected.
6. Run a full EDR scan and perform threat hunting for the listed IOCs.
7. Review scheduled-task creation events across the environment for similar task names, commands, paths, and source IP activity.

## False-Positive Considerations

- Legitimate software updaters and endpoint-management tools often create scheduled tasks.
- Approved backup, monitoring, and patching jobs may use elevated permissions.
- Confirm task ownership, software publisher, file hash, path, business purpose, and change-ticket information before taking disruptive action.

## Conclusion

Based on the simulated evidence, this alert should be escalated for incident-response investigation because it combines encoded PowerShell, external download behavior, deceptive task names, user-writable execution paths, and repeated task creation on a single workstation.
