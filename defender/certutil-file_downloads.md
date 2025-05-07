```
DeviceProcessEvents 
| where FileName =~ "certutil.exe"
| where ProcessCommandLine has_any ("-urlcache ","-verifyctl ","http://","https://")
// tweaks are needed for your env. 
| project Timestamp, DeviceId, DeviceName, ProcessCommandLine, FileName, FolderPath, InitiatingProcessFileName, InitiatingProcessFolderPath
| summarize  CommandLineCnt=count(ProcessCommandLine), ProcessCommandLine=make_set(ProcessCommandLine), FileName=make_set(FileName), FolderPath=make_set(FolderPath), InitiatingProcessFileName=make_set(InitiatingProcessFileName), InitiatingProcessFolderPath=make_set(InitiatingProcessFolderPath)
 by DeviceId, DeviceName, bin(Timestamp,2m)
```
