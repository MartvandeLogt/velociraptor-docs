---
title: Server.Internal.Notifications
hidden: true
tags: [Internal Artifact]
---

This event artifact is an internal event stream over which client
notifications are sent. A frontend will watch for events over this
stream and if a client is actively connected to this frontend, the
client will be notified that new work is available to it.

Note: This is an automated system artifact. You do not need to start it.


```yaml
name: Server.Internal.Notifications
description: |
  This event artifact is an internal event stream over which client
  notifications are sent. A frontend will watch for events over this
  stream and if a client is actively connected to this frontend, the
  client will be notified that new work is available to it.

  Note: This is an automated system artifact. You do not need to start it.

type: INTERNAL

```
