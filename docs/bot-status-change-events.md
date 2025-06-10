---
title: "Bot WebhooksMoon (Dark Mode)Sun (Light Mode)"
description: "Use bot webhook events to trigger server logic and create a real-time experience."
source_file: "docs/bot-status-change-events.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:10.745Z"
api_parameters_count: "0"
---
Recall uses bot status changes to capture the lifecycle of a bot.

These status changes are exposed through webhooks, which your application can use to create a real-time experience or react to asynchronous events outside of the API request cycle.

For example, you may want to update something on your end when a bot transitions its status from `joining_call` to `in_call_recording`. When these asynchronous events happen, we'll make a POST request to the address you give us and you can do whatever you need with it on your end.

After a webhook is configured for an environment, notifications will be sent for all events for that environment.

> **CALLOUT**:

## 🚧

Important webhook handler considerations
- **`2xx` response:** Your webhook handler should return a HTTP `2xx` Code
- **Retries:** If Recall doesn't receive a `2xx` response from your server, we will continue to try the message for the next 24 hours, with an increasing delay between attempts.
- **Timeouts:** Webhook events have a timeout of 15 seconds. If you plan to kick off longer running tasks upon receiving certain events, make sure to do this asynchronously so you respond to requests before they time out.

## Events

[](#events)

This webhook is sent whenever the bot's status is changed and is delivered via Svix to the endpoints configured in your [Recall dashboard](https://api.recall.ai/dashboard/webhooks/).

JSON

```
{
  "event": "bot.joining_call",
  // bot.in_waiting_room, bot.in_call_not_recording, bot.recording_permission_allowed
  // bot.recording_permission_denied, bot.in_call_recording, bot.call_ended
  // bot.done, bot.fatal
  "data": {
    "data": {
      "code": string,
      "sub_code": string | null,
      "updated_at": string
    },
    "bot": {
      "id": string,
      "metadata": object
    }
  }
}

```

| Event | Description |
| --- | --- |
| bot.joining_call | The bot has acknowledged the request to join the call, and is in the process of connecting. |
| bot.in_waiting_room | The bot is in the waiting room of the meeting. |
| bot.in_call_not_recording | The bot has joined the meeting, however is not recording yet. This could be because the bot is still setting up, does not have recording permissions, or the recording was paused. |
| bot.recording_permission_allowed | The bot has joined the meeting and it's request to record the meeting has been allowed by the host. |
| bot.recording_permission_denied | The bot has joined the meeting and it's request to record the meeting has been denied. Refer to the data.sub_code for the exact reason. |
| bot.in_call_recording | The bot is in the meeting, and is currently recording the audio and video. |
| bot.call_ended | The bot has left the call, and the real-time transcription is complete.The data.sub_code will contain machine readable code for why the call ended. |
| bot.done | The bot has shut down. If bot produced in_call_recording event, the video is uploaded and available for download. |
| bot.fatal | The bot has encountered an error that prevented it from joining the call. The data.sub_code will contain machine readable code for why bot failed. |

> **CALLOUT**:

## 🚧

We may add additional Status Change event codes

You should not treat the `data.code` and `data.sub_code` as an enum, as we may add values in the future without prior notice. We will never remove values without notifying all our customers and a long depreciation period, as we consider removing values a breaking change.

The list of `sub_code` & corresponding descriptions can be found here [here](/docs/sub-codes#fatal-sub-codes.md).

## Bot Status Transition Diagram

[](#bot-status-transition-diagram)

This diagram provides a detailed view of bot statuses:

![](https://files.readme.io/17216cb-Bot_Status_Transition_Flow_Chart.png)

# FAQ

[](#faq)
- * *

## Where do I find my signing secret?

[](#where-do-i-find-my-signing-secret)

Head over to the [Recall webhooks dashboard](https://api.recall.ai/dashboard/webhooks/) and click into the endpoint.

You'll find the signing secret near the bottom right hand corner:

![](https://files.readme.io/f7dd3b4-CleanShot_2024-01-14_at_21.51.202x.png)

## Can I filter which events I subscribe to?

[](#can-i-filter-which-events-i-subscribe-to)

Currently, filtering events isn't supported. This means you will receive all bot status change events for the lifecycle of your bots. If you don't need to use certain bot status change events, you can simply return a `2xx` success status code.

## Why is my webhook endpoint disabled?

[](#why-is-my-webhook-endpoint-disabled)

If all attempts to a specific endpoint fail for a period of 5 days, the endpoint will be disabled. The clock only starts after multiple deliveries failed within a 24 hour span, with at least 12 hours difference between the first and the last failure.
