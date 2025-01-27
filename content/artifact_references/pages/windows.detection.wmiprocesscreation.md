---
title: Windows.Detection.WMIProcessCreation
hidden: true
tags: [Client Event Artifact]
---

WMI Process creation is a common lateral movement technique. The
attacker simply uses WMI to call the Create() method on the
Win32_Process WMI object.

This can be easily done via the wmic.exe command or via powershell:

```bash
wmic process call create cmd.exe
```


```yaml
name: Windows.Detection.WMIProcessCreation
description: |
  WMI Process creation is a common lateral movement technique. The
  attacker simply uses WMI to call the Create() method on the
  Win32_Process WMI object.

  This can be easily done via the wmic.exe command or via powershell:

  ```bash
  wmic process call create cmd.exe
  ```

type: CLIENT_EVENT

sources:
  - query: |
        SELECT Parse from wmi_events(
          query="SELECT * FROM MSFT_WmiProvider_ExecMethodAsyncEvent_Pre WHERE ObjectPath=\"Win32_Process\" AND MethodName=\"Create\"",
          namespace="ROOT/CIMV2",
          wait=50000000)

```
