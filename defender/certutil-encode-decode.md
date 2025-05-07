```
DeviceProcessEvents
| where FileName contains "certutil"
| where ProcessCommandLine contains "decode " or ProcessCommandLine contains "encode"
```
