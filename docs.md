---
title: "Getting Started with RecallMoon (Dark Mode)Sun (Light Mode)"
description: "Record meetings, stream audio and video, generate transcripts, and so much more."
source_file: "docs.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:11.930Z"
api_parameters_count: "0"
---
[Recall](https://recall.ai) is a unified API for meeting bots.

Through Recall's API and fully managed bot infrastructure, you can easily white-label bots and send them to meetings to capture the audio, video, transcriptions, and metadata from the meeting - all through a simple API.

*For a list of all supported meeting platforms, see [Meeting Platforms](/docs/meeting-platforms.md).*

# What is a bot?

[](#what-is-a-bot)

A **bot** is the fundamental entity for accessing a given meeting's data.

Bots are single-use, and are sent to meetings either ad-hoc ("on-the-fly"), or through scheduling them for a specific time.

Through a bot, you can interface with a meeting's video, audio, participants, and metadata in real-time during a call, as well as after the call for as long as the data is [retained](/docs/data-retention.md).

# Creating and scheduling bots

[](#creating-and-scheduling-bots)

*How do I actually get bots to my meetings?*

There are two types of bots:
- **Ad-hoc bots:** These are on-demand bots, sent immediately to a meeting by making a [Create Bot](/reference/bot_create.md) request without specifying a `join_at` time.
- **Scheduled bots:** Bots can also be scheduled through the [Create Bot](/reference/bot_create.md) endpoint with a `join_at` parameter to specify when the bot should join a call.

> **CALLOUT**:

## 📘

Scheduling bots to users' calendars

Recall's [Calendar Integration](/docs/calendar-integration.md) is a layer on top of scheduled bots, allowing you to connect directly with user's calendars to automate the scheduling of bots to their calendar events.

# Video and Audio

[](#video-and-audio)

Recall bots generate a recording that can be accessed in the `media_shortcuts` field of the bot when fetched from [Retrieve Bot](/reference/bot_retrieve.md) or [List Bots](/reference/bot_list.md). The field will contain a pre-signed S3 URL that you can use to download the recording, save in your own cloud, and process accordingly.

For real-time applications, you can leverage websockets for accessing raw video and audio streams in [real-time](/docs/real-time-audio-protocol.md)

# Transcription

[](#transcription)

There are two ways to generate transcripts through Recall:
- **[Meeting Caption Transcription](/docs/meeting-caption-transcription.md):** Using the meeting platform's native closed captioning feature to generate a transcript in real-time.
- **[AI Transcription](/docs/ai-transcription.md):** Using a 3rd party AI transcription integration.

Which of these you choose depends on your requirements, and we recommend reviewing the documentation for each to decide which best fits your use case.

# Customizing your bots

[](#customizing-your-bots)

Recall bots are fully white label-able to match your branding:
- **[Output an Image](/docs/output-video-in-meetings.md):** Configure your bots to output a custom image.
- **Set the name for your bots:** Change the name of your bots by providing a `bot_name` parameter in the [Create Bot](/reference/bot_create.md) request.
