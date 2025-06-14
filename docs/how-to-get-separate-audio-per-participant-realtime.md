---
title: "How to get Separate Audio per Participant (Realtime)Moon (Dark Mode)Sun (Light Mode)"
description: "Receive audio data for each participant in realtime over websocket"
source_file: "docs/how-to-get-separate-audio-per-participant-realtime.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.243Z"
api_parameters_count: "0"
---
> **CALLOUT**:

## 📘

Audio data streaming is currently supported in raw pcm format

Audio format is **mono 16 bit signed little-endian PCM at 16khz.**

This guide is for you if:
- You want to process audio data for each participant in realtime
- You want to diarize/analyze each participant in the call individually in realtime

### Platforms Support

[](#platforms-support)

| Platform |  |
| --- | --- |
| Zoom | ✅ * Native bot only |
| Microsoft Teams | ✅ |
| Google Meet | ❌ |
| Webex | ❌ |
| Slack Huddles (Beta) | ❌ |
| Go-To Meeting (Beta) | ❌ |

# Implementation

[](#implementation)

## Step 1: Create a bot

[](#step-1-create-a-bot)

To get separate audio per participant, you must set `recording_config.audio_separate_raw = {}`. Below is an example of what it would look like in your request

cURLTypeScriptPython

```
curl --request POST \
     --url https://us-east-1.recall.ai/api/v1/bot \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --header 'authorization: YOUR_RECALL_API_KEY' \
     --data '
{
  "meeting_url": "YOUR_MEETING_URL",
  "recording_config": {
    "audio_separate_raw": {} # Add this to your request body,
    "realtime_endpoints": [
      {
      	type: "websocket", // only websocket is supported for realtime audio data
        url: YOUR_WEBSOCKET_RECEIVER_URL,
        events: ["audio_separate_raw.data"]
      }
    ]
  }
}
'

```

```
const response = await fetch("https://us-east-1.recall.ai/api/v1/bot", {
  method: "POST",
  headers: {
    "accept": "application/json",
    "content-type": "application/json"
    "authorization": "YOUR_RECALL_API_KEY" // Update this
  },
  body: JSON.stringify({
    meeting_url: "YOUR_MEETING_URL", // Update this
    recording_config: {
      video_mixed_layout: "gallery_view_v2", // Add this to your request body
      video_separate_mp4: {} # Add this to your request body
    }
  })
});

if (!response.ok) {
  throw new Error(`Error: ${response.status} ${response.statusText}`);
}

const data = await response.json();

```

```
import requests

response = requests.post(
    "https://us-east-1.recall.ai/api/v1/bot",
    json={
      "meeting_url": "YOUR_MEETING_URL", # Update this
      "recording_config": {
	      "video_mixed_layout": "gallery_view_v2" # Add this to your request body
		    "video_separate_mp4": {} # Add this to your request body
      }
    },
    headers={
      "accept": "application/json",
      "content-type": "application/json",
    	"authorization": "YOUR_RECALL_API_KEY" # Update this
    }
)

if not response.ok:
 	errorMessage = f"Error: {response.status_code} - {response.text}"
  raise requests.RequestException(errorMessage)

result = response.json()

```

## Step 2: Receive websocket messages with audio data

[](#step-2-receive-websocket-messages-with-audio-data)

Setup a websocket server and ensure it is publicly accessible. You will receive messages in the following payload format:

JSON

```
{
  "event": "audio_separate_raw.data",
  "data": {
    "data": {
      "buffer": string, // base64-encoded raw audio 16 kHz mono, S16LE(16-bit PCM LE)
      "timestamp": {
      	"relative": float,
        "absolute": string
    	},
      "participant": {
      	"id": number,
      	"name": string | null,
        "is_host": boolean,
        "platform": string | null,
        "extra_data": object
      }
    },
    "realtime_endpoint": {
      "id": string,
      "metadata": object,
    },
    "audio_separate": {
      "id": string,
      "metadata": object
    },
    "recording": {
      "id": string,
      "metadata": object
    },
    "bot": {
      "id": string,
      "metadata": object
    },
  }
}

```

> **CALLOUT**:

## 📘

Important: Connection behavior

In unmixed audio streaming, participants' audio streams connect and disconnect to your websocket endpoint according to their mute state.

For instance, a participant that remains muted on the call will only attempt to establish a websocket connection to your endpoint upon unmuting. When unmuting again, their corresponding websocket connection will be closed.
