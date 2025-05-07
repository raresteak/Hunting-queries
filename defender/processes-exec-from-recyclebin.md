Mitre: T1164.001 Hide Artifacts, T1059 Command and Scripting Int

```
DeviceProcessEvents 
| where FolderPath startswith "C:\\$Recycle.Bin\\"
| project Timestamp, DeviceName, ProcessCommandLine, InitiatingProcessFileName, FolderPath, AccountName
| sort by Timestamp desc
```
