```
DeviceNetworkEvents
| where RemotePort == 5985
| where InitiatingProcessFileName contains "powershell"
| where RemoteIP !has "::1"
| where RemoteIP !has "127.0.0.1"
| project Timestamp, InitiatingProcessAccountName, InitiatingProcessFileName, DeviceName, RemoteIP, RemoteUrl, RemotePort, InitiatingProcessAccountUpn
```

tweaking may be needed
