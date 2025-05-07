DeviceEvents
| where ActionType has "ScheduledTaskCreated"
//| where InitiatingProcessAccountName !endswith "$"
// tuning required to remove known goodware
//| where not (AdditionalFields has_any (@"\\WinZip Updater - ", @"\\OneDrive Per-Machine Standalone Update Task", @"\\Mozilla\\Firefox Background Update", @"\\MicrosoftEdgeUpdateTaskUserS-1-5-21"))
| extend TaskName = split(AdditionalFields,",")[0]
| where TaskName !contains "ZoomUpdateTaskUser-S-1-5-21"
| where TaskName !contains "GoogleUpdaterTaskUser1"
| extend UserName = split(AdditionalFields,",")[-1]
| extend command = split(AdditionalFields,",")[-3]
| extend arguments = split(AdditionalFields,",")[-2]
| project Timestamp, DeviceName, TaskName, UserName, command, arguments, AdditionalFields
| sort by Timestamp desc 
