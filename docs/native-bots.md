---
title: "Native BotsMoon (Dark Mode)Sun (Light Mode)"
description: "Bots come in two varieties: Native and Web . Web bots: The default meeting bot. Recommended for a vast majority of use cases. Native bots: A distinct type of bot that enables native-specific features specifically for Zoom. Only for a small minority of use cases. Web bots are enabled by default and t..."
source_file: "docs/native-bots.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.437Z"
api_parameters_count: "0"
---
Bots come in two varieties: **Native** and **Web**.

**Web bots:** The default meeting bot. Recommended for a vast majority of use cases.

**Native bots:** A distinct type of bot that enables native-specific features specifically for Zoom. Only for a small minority of use cases.

Web bots are enabled by default and typically work well for most use cases. If your application requires Native bot features, such as separate audio streams, this guide will help you get up and running with Native bots.

# How to configure native bots

[](#how-to-configure-native-bots)

You can configure a Zoom Native bot through the `variant` parameter in your [Create Bot](/reference/bot_create.md) request:

cURL

```
curl --request POST \
     --url https://us-east-1.recall.ai/api/v1/bot/ \
     --header "Authorization: $RECALLAI_API_KEY" \
     --header "accept: application/json" \
     --header "content-type: application/json" \
     --data '
{
  "meeting_url": "https://zoom.us/j/123456789",
  "variant": {
    "zoom": "native"
  }
}
'

```

# Limitations

[](#limitations)

Currently Zoom Native bots have the following limitations:
- Cannot [Output Audio](/reference/bot_output_audio_create.md)
- Cannot [Receive Chat Messages](/docs/receiving-chat-messages.md)
- Cannot [Output Media](/reference/bot_output_media_create.md)
- Cannot receive audio from dialed-in participants\*

*\*Limitation of Zoom Meeting SDK for Linux*
