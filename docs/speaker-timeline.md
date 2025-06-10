---
title: "Speaker TimelinesMoon (Dark Mode)Sun (Light Mode)"
description: "Use speaker timelines to know when participants are speaking."
source_file: "docs/speaker-timeline.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:11.662Z"
api_parameters_count: "0"
---
A speaker timeline is a history of active speaker events for a bot.

Recall uses this timeline for transcript [diarization](/docs/diarization.md), and also exposes it through the Participant Events resource associated with the recording.

## Timestamps

[](#timestamps)

The timestamp for each active speaker events is offset in seconds relative to the bot's `in_call_recording` event.

## Fetching the speaker timeline

[](#fetching-the-speaker-timeline)

After calling [Retrieve Bot](/reference/bot_retrieve.md), you can download a speaker timeline from the `media_shortcuts.participant_events.data.speaker_timeline_download_url` field in the `recordings` object(s). View the response format [response format here](/docs/download-schemas#json-speaker-timeline-download-url.md).
