---
title: "Real-time Video: RTMPMoon (Dark Mode)Sun (Light Mode)"
description: "Currently RTMP only supports a single, mixed video/audio. Configure the bot Now it's time to send a bot to a meeting while configuring a real-time websocket endpoint. To do this, call the Create Bot endpoint while providing a real-time endpoint object where: type : rtmp config.url : Your publicly ex..."
source_file: "docs/stream-real-time-video-rtmp.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.849Z"
api_parameters_count: "0"
---
Currently RTMP only supports a single, mixed video/audio.

# Configure the bot

[](#configure-the-bot)

Now it's time to send a bot to a meeting while configuring a real-time websocket endpoint.

To do this, call the [Create Bot](/reference/bot_create.md) endpoint while providing a real-time endpoint object where:
- **`type`:** `rtmp`
- **`config.url`:** Your publicly exposed ngrok tunnel URL
- **`config.events`:** An array including the `video_mixed_flv.data` event

Include `video_mixed_flv` media object in `recording_config` . Don't forget to set `meeting_url` to your newly-created Google Meet call.

**Example curl:**

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
    "video_mixed_flv": {},
    "realtime_endpoints": [
      {
        "type": "rtmp",
        "config": {
          "url": "rtmps://your-app.com/api/...",
          "events": ["video_mixed_flv.data"]
        }
      }
    ]
  }
}
'

```

Your RTMP destination URL should have the following format:

`rtmp://hostname[:port]/{APPLICATION-NAME}/{STREAM-KEY}`
