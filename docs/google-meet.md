---
title: "Google Meet OverviewMoon (Dark Mode)Sun (Light Mode)"
description: "Google Meet Bots Overview"
source_file: "docs/google-meet.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.198Z"
api_parameters_count: "0"
---
# Setup

[](#setup)

> **CALLOUT**:

## ✅

No setup required

Recall supports Google Meet bots out-of-the-box, no setup or configuration needed.

# Recording Behavior

[](#recording-behavior)

**No recording permission** is needed for Google Meet calls.

This means that as long as the bot is in the call, it will be able to record.

# Joining Behavior

[](#joining-behavior)

By default, Google Meet bots need to be **manually admitted** into calls and will be an "anonymous" user.

**When a bot attempts to join a Google Meet call, this dialog will be displayed to participants:**

![](https://files.readme.io/65a5e7b-Screen_Shot_2023-03-18_at_7.56.55_PM.png "Screen Shot 2023-03-18 at 7.56.55 PM.png")



Any signed in participant in the host's Google Workspace can let the bot in.

If you want the bot to automatically join Google Meet calls, the bot must be [Authenticated](/docs/google-meet-login-getting-started.md).

Authenticated bots are still subject to any waiting room settings enabled by the host.

# Limitations

[](#limitations)

## Google Meet Livestreams

[](#google-meet-livestreams)

A [Google Meet livestream](https://support.google.com/meet/answer/9308630?hl=en&co=GENIE.Platform%3DDesktop) allows users to broadcast a video meeting to a large audience in a view-only format. This is particularly useful for events where interaction is not required from the viewers, such as webinars.

Google meet livestreams are currently not supported.

## Breakout Rooms

[](#breakout-rooms)

Google Meet breakout rooms are not currently supported.
