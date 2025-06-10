---
title: "AI TranscriptionMoon (Dark Mode)Sun (Light Mode)"
description: "Use one of Recall's AI transcription partners to generate meeting transcripts"
source_file: "docs/ai-transcription.html"
is_api_reference: "false"
converted_at: "2025-06-10T14:00:10.964Z"
api_parameters_count: "0"
---
In addition to meeting caption transcriptions, Recall also integrates with several AI transcription partners as a solution for producing transcripts, as well as meeting intelligence such as summarization and sentiment analysis.

There are two options for transcription when using one of our AI transcription partners:

1.  **[Real-time transcription](/docs/real-time-transcription)** : Transcript is generated in real-time.
2.  **[Async Transcription](/docs/async-transcription)**: Transcript is generated after the call has completed.

Both methods have pros and cons, and which you choose will ultimately depend on your use case.

If you don't have a need for receiving transcripts in real-time, we recommend starting with asynchronous transcription, as it's generally more accurate and cost effective.

> **CALLOUT**:

## ❗️

Important: Concurrency considerations

When going to production, make sure that your account with your 3rd party transcription provider is configured with high enough concurrency limit to support your anticipated load.

Certain transcription providers require that you reach out to increase your concurrency limit, and we highly recommend checking this prior to running production workloads.

# AI Transcription Providers

[](#ai-transcription-providers)

To use a given transcription provider, you can add an API key for the provider in the Recall dashboard using their corresponding dashboard link.

| Provider | Provider Information | Regions |
| --- | --- | --- |
| Assembly AI | AssemblyAI Pricing | api.assemblyai.com |
| AWS Transcribe | AWS Transcribe Pricing | Any supported AWS region |
| Deepgram | Deepgram Pricing | On Param |
| Gladia | Gladia Pricing | api.gladia.ai |
| Rev | Rev Pricing | api.rev.ai |
| Speechmatics | Speechmatics Pricing | eu2.rt.speechmatics.com |

> **CALLOUT**:

## 👍

Once your credentials are set, you're ready to create your first [Real-Time](/docs/real-time-transcription) or [Async](/docs/async-transcription) transcript.
