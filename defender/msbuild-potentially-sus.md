```
DeviceProcessEvents
| where FileName has "msbuild.exe"
| where ProcessCommandLine contains ".xml" or ProcessCommandLine contains ".csproj" or ( ProcessCommandLine contains "/logger" and ProcessCommandLine contains ".dll" ) or ProcessCommandLine contains ".proj" or ProcessCommandLine contains ".rsp"
```
