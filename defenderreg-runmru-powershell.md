```
DeviceRegistryEvents
| where RegistryKey contains "\\Software\\Microsoft\\Windows\\CurrentVersion\\Explorer\\RunMRU"
| where RegistryValueData contains "powershell" or PreviousRegistryValueData contains "powershell"
```
