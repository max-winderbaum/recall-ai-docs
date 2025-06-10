---
title: "Real-Time Websocket EndpointsMoon (Dark Mode)Sun (Light Mode)"
description: "Receive recording data and events in real-time via websockets"
source_file: "docs/real-time-websocket-endpoints.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:00:11.903Z"
api_parameters_count: "0"
---
In addition to [Webhooks](/docs/real-time-webhook-endpoints), Recall.ai supports receiving data in real-time via a websocket connection.

You can register a websocket real-time endpoint during data source creation (for instance, when [Creating a Bot](/reference/bot_create), specifying the specific events you want to receive.

# Event Types

[](#event-types)

Real-time websocket endpoints can subscribe to all of the following events:

| Event | Description | Payload |
| --- | --- | --- |
| participant_events.join | A participant joined. | Schema |
| participant_events.leave | A participant left. | Schema |
| participant_events.update | A participant updated their details. | Schema |
| participant_events.speech_on | A participant started speaking. | Schema |
| participant_events.speech_off | A participant stopped speaking. | Schema |
| participant_events.webcam_on | A participant turned on their webcam. | Schema |
| participant_events.webcam_off | A participant turned off their webcam. | Schema |
| participant_events.screenshare_on | A participant started screen sharing. | Schema |
| participant_events.screenshare_off | A participant stopped screen sharing. | Schema |
| participant_events.chat_message | A participant sent a chat message. | Schema |
| transcript.data | A transcript utterance was generated (see Real-time Transcription | Schema |
| audio_mixed_raw.data | A mixed audio buffer was generated from the call. | Schema |
| audio_separate_raw.data | A separate audio buffer was generated from the call. | Schema |
| video_separate_png.data | A separate video buffer was generated from the call. | Schema |

# Setup & Configuration

[](#setup--configuration)
- * *

## Bots

[](#bots)

To configure a real-time websocket endpoint for a bot, add a real time endpoint to your [Create Bot](/reference/bot_create) request with the `type` set to `websocket`:

cURL

```
curl --request POST \
     --url https://us-east-1.recall.ai/api/v1/bot/ \
     --header "Authorization: $RECALLAI_API_KEY" \
     --header "accept: application/json" \
     --header "content-type: application/json" \
     --data '
{
  "meeting_url": "https://meet.google.com/sde-zixx-iry",
  "recording_config": {
	  "realtime_endpoints": [
      {
        "type": "websocket",
        "url": "wss://my-app.com/api/ws/audio",
        "events": ["audio_mixed_raw.data"]
      }
    ]
  }
}
'

```

The above request creates a bot and registers a real-time websocket endpoint to receive `audio_mixed_raw.data` events at the following URL: `wss://my-app.com/api/ws/audio`

> **CALLOUT**:

## 📘

The `config.url` must be either a `ws` or `wss` endpoint.

# Verification

[](#verification)

Since your websocket receiver must be accessible at a publicly exposed URL, you must add a verification mechanism to ensure you only accept connections coming from Recall.

To do this, provide a secret or token as a query parameter in the endpoint's URL, such as `token=some-random-token`.

When we make the request to connect to your endpoint, we will use the **exact** url, including any query parameters. You will then be able to verify the query parameter in your server's websocket handler, and reject any requests that do not contain your secret/token value.

# Retry Policy

[](#retry-policy)

Recall attemps to maintain a persistent WebSocket connection and will retry automatically upon connection failure using the following policy:

**Retry condition**: A retry is triggered when the WebSocket connection fails due to:
- Network interruptions
- Server-side disconnects
- Failed connection handshake

**Retry limit**: A maximum of 30 retry attempts are made per connection failure incident.

**Backoff strategy**: Each retry is delayed by a fixed **3-second interval**.

**Dropping behavior**: If all **30 attempts fail**, the realtime endpoint is marked as `failed` and no further messages are delivered
