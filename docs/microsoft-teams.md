---
title: "Teams OverviewMoon (Dark Mode)Sun (Light Mode)"
description: "Overview of Microsoft Teams Bots."
source_file: "docs/microsoft-teams.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.431Z"
api_parameters_count: "0"
---
# Setup

[](#setup)

> **CALLOUT**:

## ✅

No setup needed

Teams Web bots work "out-of-the-box," no setup or configuration needed.

# Recording Behavior

[](#recording-behavior)

**No recording permission** is needed for Microsoft Teams calls.

This means that as long as the bot is in the call, it will be able to record.

# Joining Behavior

[](#joining-behavior)

By default, Microsoft Teams bots will need to be let in from the lobby.

Authenticated Teams bots are still subject to any lobby settings enabled by the host. For instance, the host can still require that *all* participants enter through the waiting room.

# Limitations

[](#limitations)
- * *

## Screen share capture limitations

[](#screen-share-capture-limitations)

Microsoft Teams has a more native screensharing capability that allows users to share certain applications and documents directly, instead of the typical screenshare modes of capturing a window or their entire screen.

Teams bots currently do not support capturing these, since they use a different mechanism than sharing your screen, window, or tab.

These limitations include:
- Microsoft Whiteboard
- Powerpoint live
- Excel Live

![These screensharing options are not yet supported.](https://files.readme.io/52526f1-Screenshot_2024-07-19_at_4.18.54_PM.png)

These screensharing options are not yet supported.

## Registration-required meetings & webinars

[](#registration-required-meetings--webinars)

Meetings and webinars that require registration are currently not supported.



## Teams breakout rooms

[](#teams-breakout-rooms)

Teams breakout rooms are currently not supported.
