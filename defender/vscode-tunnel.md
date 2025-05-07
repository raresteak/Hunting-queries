```
DeviceProcessEvents
| where (( FileName has "code.exe" or InitiatingProcessVersionInfoInternalFileName has "electron.exe") and ProcessCommandLine contains " tunnel" ) or FileName has "code-tunnel.exe"
| where ProcessCommandLine contains "--name "
| project Timestamp, DeviceName, ProcessCommandLine, AccountName, DeviceId, ReportId
| sort by Timestamp asc 
// Other IOC:
// User agents observed in proxy traffic
// VisualStudioTunnelCreation 
// vscode.dev.remote-server Dev-Tunnels-Service-TypeScript-SDK/
// DNS 
// *.tunnels.api.visualstudio.com
// Users testing their tunnel
// https://vscode.dev/tunnel/
```
