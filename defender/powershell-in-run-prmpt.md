```
DeviceRegistryEvents
| where RegistryKey contains "\\Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\RunMRU"
| where RegistryValueData contains "powershell" or PreviousRegistryValueData contains "powershell"
//hunts for powershell commands in the windows run prompt (CTRL+r) being executed. 
```
