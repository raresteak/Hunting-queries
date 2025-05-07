```
DeviceProcessEvents
| where FileName has "msiexec.exe"
//| where ProcessCommandLine contains "/quiet"
| where ProcessCommandLine contains " http" or (ProcessCommandLine contains " /y " and ProcessCommandLine contains ".dll ") or (ProcessCommandLine contains " /z " and ProcessCommandLine contains ".dll ")
```
