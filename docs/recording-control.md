---
title: "Recording ControlMoon (Dark Mode)Sun (Light Mode)"
description: "Control when your bot records using the Pause/Resume and Start/Stop recording endpoints."
source_file: "docs/recording-control.html"
is_api_reference: "false"
converted_at: "2025-06-10T18:47:15.666Z"
api_parameters_count: "0"
---
Some use cases require having more granular control over when a bot records.

To support use cases that require more granular control over when a bot records, Recall provides 2 mechanisms:

1.  **Pause/Resume Recording**
2.  **Start/Stop Recording**

> **CALLOUT**:

## 📘

Real-time transcription and recording

When a bot isn't recording (is paused or stopped), real-time transcription will also be halted until recording begins again.

# Pause & Resume Recording

[](#pause--resume-recording)
- * *

> **CALLOUT**:

## 📘

The pause and resume recording endpoints allow you to control when a bot is recording, while still generating a *single* recording.

These endpoints are the recommended approach for generating a continuous recording of separate segments of a meeting.

[Pause Recording](/reference/bot_pause_recording_create.md) pauses the current recording.

[Resume Recording](/reference/bot_resume_recording_create.md) resumes the *same* recording.

The result is a single recording file containing video/audio only from segments where the bot was not paused.

## FAQs

[](#faqs)

### Why is there a silent black screen in my recording?

[](#why-is-there-a-silent-black-screen-in-my-recording)

This is the time the video was paused and the bot did not record the meeting.

### When I pause and then resume the recording, how does the transcript timestamp correlate to the recorded video?

[](#when-i-pause-and-then-resume-the-recording-how-does-the-transcript-timestamp-correlate-to-the-recorded-video)

The timestamps in the transcript align with the recorded video, which includes the black screen time. If you remove the black screen clip from the recording, you will also need to offset the transcript timestamps too

# Start & Stop Recording

[](#start--stop-recording)
- * *

[Start Recording](/reference/bot_start_recording_create.md) triggers the bot to start recording. If a bot is already recording when this endpoint is called, a *new* recording will begin, overwriting the old recording.

[Stop Recording](/reference/bot_stop_recording_create.md) stops the current recording of the bot and creates a new recording entry in the `recordings` field of the [bot](/reference/bot_retrieve.md).

> **CALLOUT**:

## 📘

Accessing individual recordings

In the [Retrieve Bot](/reference/bot_retrieve.md) response, the `recordings` field will contain the separate recordings, and you can access the corresponding video for each in the `media_shortcuts.video_mixed.data.download_url` field.

For a single, contiguous recording of multiple recording segments, you should use [Pause & Resume Recording](#pauseresume-recording) .

## Control when the bot starts recording

[](#control-when-the-bot-starts-recording)

You may require a flow where you have a user action trigger when a bot starts recording.

For example, if you require everyone in the call to manually opt-in to recording via verbal confirmation or via email prior to the call.

In this case, you can:

1.  Set `recording_config.start_recording_on` to `manual` when calling [Create Bot](/reference/bot_create.md)
2.  Have a check in your application's logic to call [Start Recording](/reference/bot_start_recording_create.md) if and when your start recording criteria have been met.
