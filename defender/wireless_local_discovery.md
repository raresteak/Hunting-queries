```
DeviceProcessEvents
| where ( FileName has "netsh.exe" and ProcessCommandLine contains "show" and ProcessCommandLine contains "profiles" and ProcessCommandLine contains "key=clear") or ( FileName has "netsh.exe" and ProcessCommandLine contains "hostednetwork" ) or ProcessVersionInfoFileDescription contains "extracts wireless keys" or ProcessVersionInfoProductName contains "wireless key view"
| project Timestamp, DeviceName, ProcessCommandLine, ProcessIntegrityLevel, InitiatingProcessParentFileName, AccountName, AccountUpn, DeviceId, ReportId
```
