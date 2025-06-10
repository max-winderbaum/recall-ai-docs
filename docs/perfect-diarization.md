---
title: "Perfect DiarizationMoon (Dark Mode)Sun (Light Mode)"
description: "📘 Supported Platforms: Perfect diarization is currently supported for Zoom Native and Teams Web bots. Perfect diarization is a feature designed to address the problem of inaccurate speaker attribution in meeting transcripts. Meeting platforms can sometimes attribute words to the wrong speaker, espe..."
source_file: "docs/perfect-diarization.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:47:11.394Z"
api_parameters_count: "0"
---
> **CALLOUT**:

## 📘

Supported Platforms

Perfect diarization is currently supported for Zoom Native and Teams Web bots.

Perfect diarization is a feature designed to address the problem of inaccurate speaker attribution in meeting transcripts. Meeting platforms can sometimes attribute words to the wrong speaker, especially when multiple people are talking at once. This feature ensures that each speaker's words are accurately identified, even when participants are talking over each other.

## How It Works

[](#how-it-works)

Perfect diarization transcribes separate audio streams for each participant instead of using the combined audio stream for the entire meeting, significantly improving the accuracy of speaker attribution.

This feature is compatible with all [AI transcription providers](/docs/ai-transcription#ai-transcription-providers.md) supported by Recall.ai and can be used for [real-time transcription](/docs/real-time-transcription.md).

## Usage

[](#usage)

To configure perfect diarization in a [Create Bot](/reference/bot_create.md) request, set the `use_separate_streams_when_available` to `true` in your `recording_config.transcript.diarization` config:

JSON

```
curl --request POST \
     --url https://us-east-1.recall.ai/api/v1/bot/ \
     --header "Authorization: $RECALLAI_API_KEY" \
     --header "accept: application/json" \
     --header "content-type: application/json" \
     --data '
{
  "recording_config": {
    "transcript": {
      "diarization": {
        "use_separate_streams_when_available": true
      },
      "provider": {
        ...
      }
    }
  }
}
'

```

## Important Considerations

[](#important-considerations)

**Increased Transcription Usage:** Transcribing multiple streams may result in higher costs from your transcription provider. On average, usage is ~1.8x higher than single-stream transcription.
