---
title: "Bypass the Teams LobbyMoon (Dark Mode)Sun (Light Mode)"
description: "Enable bots to bypass the Microsoft Teams lobby."
source_file: "docs/guides.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.205Z"
api_parameters_count: "0"
---
There are two ways for Microsoft Teams bots to be able to bypass the lobby:

1.  Authenticate bots using [Microsoft Teams Bot Login](/docs/microsoft-teams-bot-login-getting-started.md)
2.  Have the end user allow everyone to bypass the lobby



**Below shows the Microsoft Teams settings for lobby behavior**
- **Green:** Bots will be able to join without authenticating if the end user changes their setting to "Everyone"
- **Red:** Bots will bypass the lobby only if they're authenticated, otherwise they will go through the lobby

![](https://files.readme.io/4eb314c-CleanShot_2024-02-21_at_15.39.342x.png)
