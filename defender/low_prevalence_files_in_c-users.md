```
DeviceFileEvents
| where (FolderPath startswith "c:\\users\\" ) and (FileName endswith ".msi" or FileName endswith ".zip) //tweak
| where ActionType == "FileCreated" or ActionType == "FileRenamed"
| extend subdirs_index = split(FolderPath, "\\")
| extend subdirs_cnt = array_length(subdirs_index)
// | where subdirs_cnt <= 6 // use this to control depth of analysis
| project CreatedOn = Timestamp, FileName, FolderPath, SHA1
| invoke FileProfile("SHA1", 1000) 
//| where Signer != "Microsoft Corporation" // tweaks
//| where Signer != "Google LLC" // tweaks
| where GlobalPrevalence < 6 // tweaks
| project CreatedOn, FileName, FolderPath, GlobalPrevalence, Signer, SoftwareName, FileSize, SHA256, GlobalFirstSeen, GlobalLastSeen
| sort by CreatedOn
//| summarize count()by SHA1
// Lots of exclusions are needed for known goodware
```
