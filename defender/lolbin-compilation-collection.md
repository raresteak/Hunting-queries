```
DeviceProcessEvents
| where 
      ( FileName has "vbc.exe" and ( ProcessCommandLine contains "/target" or ProcessCommandLine contains "-reference")) 
   or ( FileName has "ilasm.exe" and ( ProcessCommandLine contains "/exe" or ProcessCommandLine contains "/dll")) 
   or ( FileName has "jsc.exe" ) 
   or ( FileName has "csc.exe" and ProcessCommandLine contains ".cs"  and ProcessCommandLine !contains "\\shimgen\\"  and (ProcessCommandLine contains "out:" or ProcessCommandLine contains "target:"))
| join kind=inner DeviceFileEvents on DeviceName
| where InitiatingProcessCommandLine1 == ProcessCommandLine
| where ActionType1 has "FileCreated" and ( InitiatingProcessCommandLine1 has "vbc.exe" or InitiatingProcessCommandLine1 has "iliasm.exe" or InitiatingProcessCommandLine1 has "jbc.exe" or InitiatingProcessCommandLine1 has "csc.exe")
| project Timestamp1, DeviceName1, ActionType1, FileName1, FolderPath1, SHA1, ProcessCommandLine, InitiatingProcessAccountName
```
