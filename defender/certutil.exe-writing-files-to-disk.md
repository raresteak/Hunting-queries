```
DeviceFileEvents
| where InitiatingProcessFileName has "certutil.exe"
| project Timestamp, DeviceName, InitiatingProcessCommandLine, InitiatingProcessParentFileName, ActionType, ReportId, DeviceId
```
