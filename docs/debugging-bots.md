---
title: "Debugging BotsMoon (Dark Mode)Sun (Light Mode)"
description: "Figure out why your bot didn't behave as expected."
source_file: "docs/debugging-bots.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.010Z"
api_parameters_count: "0"
---
There are a number of places a bot can run into trouble, and it's not always obvious why a bot was unable to join a call or failed to record.

Since each meeting platform has its own settings, constraints, and limitations, Recall provides tools to help you figure out where a bot went wrong so that you can take action to fix it.

# Explorer dashboard

[](#explorer-dashboard)

To get more visibility into a bot without having to make API requests and inspect them, you can search the bot ID using the [explorer dashboard](https://api.recall.ai/dashboard/explorer/).

In the dashboard, you can search a specific bot ID to view the bot's information, including the status changes, recording, transcript, debug screenshots, and bot logs.

For a URL-based search, you can jump to a bot in the explorer by adding the bot as a path parameter:

```
https://us-east-1.recall.ai/dashboard/explorer/bot/{BOT_ID}

```

# Status change events

[](#status-change-events)

> **CALLOUT**:

## 📘

[Bot Status Changes](/docs/bot-status-change-events.md) capture the lifecycle of a bot and expose it via the API and webhook events.

Besides the typical, default behavior of a bot joining a call, starting recording, and so on, bots can also contain status changes that provide insight into the errors when a bot fails to record or is unable to join a call.

Status changes with a **`fatal`** code will have a **`sub_code`** explaining the reason that the error occurred. A list of all possible sub codes can be found at [Bot Sub Codes](/reference/subcodes.md).

To see a bot's status changes, call the [Retrieve Bot](/reference/bot_retrieve.md) endpoint and view the `status_changes` array in the bot object:

JSON

```
{
  "bot_id": "...",
  "status_changes": [
    ...
    {
      "code": "joining_call",
      "message": null,
      "created_at": "2024-02-17T16:44:00.505440Z",
      "sub_code": null
    },
    {
      "code": "in_waiting_room",
      "message": null,
      "created_at": "2024-02-17T16:44:17.692342Z",
      "sub_code": null
    },
    {
      "code": "in_call_not_recording",
      "message": null,
      "created_at": "2024-02-17T16:44:23.288984Z",
      "sub_code": null
    },
    {
      "code": "in_call_recording",
      "message": null,
      "created_at": "2024-02-17T16:44:23.295099Z",
      "sub_code": null
    },
    ...
  ],
  ...
}

```

# Bot Screenshots

[](#bot-screenshots)

Bot screenshots give you the bot's point-of-view throughout the duration of a the call.

Screenshots **do not include participant video** and are meant for debugging.

They're particularly useful for:
- Seeing why a bot was unable to join a call if it's unclear from its `status_changes`
- Checking on a bot that appears to be in a weird or unknown state

To get a list of screenshots associated with a bot, you can call [List Bot Screenshots](/reference/bot_screenshots_list.md).

**Note: Zoom Native bots do not provide debug screenshots.**
