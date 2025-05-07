```
WindowsEvent
| where EventID == 4688
| where  ( EventData.NewProcessName contains "quser.exe" and EventData.CommandLine contains "server:" ) or ( EventData.CommandLine contains "query" and EventData.CommandLine contains "user" and EventData.CommandLine contains "server:" )
| project TimeGenerated, Computer,EventData.CommandLine, EventData.SubjectUserName
| summarize dcount(tostring(EventData_CommandLine)) by Computer
| where dcount_EventData_CommandLine >= 2 // number of unique endpoints the source system is connecting to.  Adjust to your needs. 
| join WindowsEvent on Computer
| where EventID == 4688
| where ( EventData.NewProcessName contains "quser.exe" and EventData.CommandLine contains "server:" ) or ( EventData.CommandLine contains "query" and EventData.CommandLine contains "user" and EventData.CommandLine contains "server:" )
| project TimeGenerated, Computer,EventData.CommandLine, EventData.SubjectUserName
// Mitre T1033 - User Discovery
```
