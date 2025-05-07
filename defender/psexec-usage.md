```
DeviceProcessEvents 
| where FileName =~ "psexec" or ProcessCommandLine contains "psexec"
| where ProcessCommandLine has_any ("-accepteula","-c ","-s ","-u ","-r ","-p ")
| project Timestamp, DeviceId, DeviceName, ProcessCommandLine, FileName, FolderPath, InitiatingProcessFileName, InitiatingProcessFolderPath
| summarize  CommandLineCnt=count(ProcessCommandLine), ProcessCommandLine=make_set(ProcessCommandLine), FileName=make_set(FileName), FolderPath=make_set(FolderPath), InitiatingProcessFileName=make_set(InitiatingProcessFileName), InitiatingProcessFolderPath=make_set(InitiatingProcessFolderPath)
 by DeviceId, DeviceName, bin(Timestamp,2m)
```

tweaks may be needed. 
