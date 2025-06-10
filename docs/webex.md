---
title: "Webex OverviewMoon (Dark Mode)Sun (Light Mode)"
description: "Send meeting bots to Webex calls."
source_file: "docs/webex.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:00:12.224Z"
api_parameters_count: "0"
---
> **CALLOUT**:

## 🛠️

Setup required

Webex bots are not supported "out-of-the-box" and require some initial setup.

To start sending bots to Webex calls, follow the [Webex Bot Setup](/docs/webex-bot-setup) guide.



# Limitations

[](#limitations)
- * *

Before getting started with Webex bots, there are some important limitations to be aware of.

## Active speaker events

[](#active-speaker-events)

Active speaker events will only be available if the meeting host:
- Is on a **paid** Webex account
- Has closed captions turned **on** for the meeting

## Audio limitations

[](#audio-limitations)

Webex only supports a single, combined stream of audio.

`automatic_audio_output` in [Create Bot](/reference/bot_create) is not supported.

## Video limitations

[](#video-limitations)

Webex only supports one combined video stream with no support for layout configuration.

The current behavior is video of the active speaker in the call (prominent) + up to 6 other video participants (in footer tray).

## Caption limitations

[](#caption-limitations)

Captions through Webex's native transcription service are currently not supported. To transcribe a conversation in real-time on a Webex meeting, you'll need to use one of the [AI Transcription Providers](/docs/ai-transcription#ai-transcription-providers).
