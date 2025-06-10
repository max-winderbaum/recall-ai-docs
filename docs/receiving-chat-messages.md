---
title: "Receiving Chat MessagesMoon (Dark Mode)Sun (Light Mode)"
description: "Platform Support Platform Supported Limitations Zoom ✅ Receiving chat messages in the Zoom Native Bot is not currently supported Google Meet ✅ Microsoft Teams ✅ Bots can only receive chat messages if the meeting chat is accessible to anonymous participants. Cisco Webex ❌ Slack Huddles ❌ Setup &amp; ..."
source_file: "docs/receiving-chat-messages.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.659Z"
api_parameters_count: "0"
---
# Platform Support

[](#platform-support)

| Platform | Supported | Limitations |
| --- | --- | --- |
| Zoom | ✅ | Receiving chat messages in the Zoom Native Bot is not currently supported |
| Google Meet | ✅ |  |
| Microsoft Teams | ✅ | Bots can only receive chat messages if the meeting chat is accessible to anonymous participants. |
| Cisco Webex | ❌ |  |
| Slack Huddles | ❌ |  |

# Setup & Configuration

[](#setup--configuration)

To receive chat message webhooks, set a [Real-Time Webhook Endpoint](/docs/real-time-webhook-endpoints.md) with the `participant_events.chat_message` event when calling [Create Bot](/reference/bot_create.md):

cURL

```
curl --request POST \
     --url https://us-east-1.recall.ai/api/v1/bot/ \
     --header "Authorization: $RECALLAI_API_KEY" \
     --header "accept: application/json" \
     --header "content-type: application/json" \
     --data '
{
  "meeting_url": "https://meet.google.com/hzj-adhd-inu",
  "recording_config": {
    "realtime_endpoints": [
      {
        "type": "webhook",
        "url": "https://my-app.com/api/webhook/recall",
        "events": ["participant_events.chat_message"]
      }
    ]
  }
}
'

```

Then, **as long as the bot is in the `in_call_recording` state**, the configured endpoint will receive chat messages as webhook events.



# Event Payload

[](#event-payload)

Whenever a message readable by the bot is received in the chat, your endpoint will receive a webhook event with the following payload:

JSON

```
{
  "event": "participant_events.chat_message", // participant_events.join, participant_events.leave, participant_events.speech_on, participant_events.speech_off (& more)
  "data": {
    "data": {
      "participant": {
      	"id": number,
      	"name": string | null,
        "is_host": boolean,
        "platform": string | null,
        "extra_data": object
    	},
      "timestamp": {
        "absolute": string,
        "relative": float
      },
      "data":
      	{
          "text": string,
          "to": string
        } // populated for `participant_events.chat_message` event
      	| null
    },
    // The real-time endpoint configured to receive data
    "realtime_endpoint": {
      "id": string,
      "metadata": object,
    },
    // The associated ParticipantEvents Resource encapsulating this data
    "participant_events": {
      "id": string,
      "metadata": object
    },
    "recording": {
      "id": string,
      "metadata": object
    },
    // The related bot, if the recording is produced by a bot
    "bot": {
      "id": string,
      "metadata": object
    }
  }
}

```
