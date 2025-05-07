```
DeviceProcessEvents
| where FileName has "csc.exe"
| where ProcessCommandLine contains "out:" or ProcessCommandLine contains "/?" or ProcessCommandLine contains "target:" or ProcessCommandLine contains ".cs" or ProcessCommandLine contains "help "
```


Baseling in your env. should be done.  /? and help,  is looking for hands on keyboard or in experianced operators trying to get help which may result in false positives if you expect csc.exe usage. 
