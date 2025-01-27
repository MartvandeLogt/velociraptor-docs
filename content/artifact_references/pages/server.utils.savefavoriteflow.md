---
title: Server.Utils.SaveFavoriteFlow
hidden: true
tags: [Client Artifact]
---

Users may collect various artifacts from hosts. Sometimes it might
take a bit of effort to setup and configure just the perfect
combination of parameters and artifacts to collect.

This artifact allows the user to save the collection into a
Favorites section, which may be used in future.


```yaml
name: Server.Utils.SaveFavoriteFlow
description: |
  Users may collect various artifacts from hosts. Sometimes it might
  take a bit of effort to setup and configure just the perfect
  combination of parameters and artifacts to collect.

  This artifact allows the user to save the collection into a
  Favorites section, which may be used in future.

parameters:
  - name: Specs
    type: json_array
    description: The collection request that will be recreated.
  - name: Name
    description: A name for this collection template
  - name: Description
    description: A description for the template.
  - name: Type
    description: The type of favorites to save.
    type: choices
    default: CLIENT
    choices:
      - CLIENT
      - SERVER
      - CLIENT_EVENT
      - SERVER_EVENT

sources:
  - query: |
      SELECT favorites_save(
         name=Name,
         description=Description,
         specs=Specs,
         type=Type)
      FROM scope()

```
