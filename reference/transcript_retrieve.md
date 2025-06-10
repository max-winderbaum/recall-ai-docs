---
title: "Retrieve TranscriptMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/transcript_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:15.274Z"
api_parameters_count: "29"
---
## GET https://us-east-1.recall.ai/api/v1/transcript/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this transcript artifact. |
| recording | object | Yes |  |
| metadata | object \| null | Yes |  |
| created_at | date-time | Yes |  |
| status | object | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| code | string | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| sub_code | string \| null | Yes |  |
| updated_at | date-time | Yes |  |
| data | object | Yes | Download transcript for the recording. See response format here |
| download_url | uri \| null | Yes | Download transcript for the recording. See response format here |
| provider_data_download_url | uri \| null | Yes | Download raw transcription data received from the provider for the recording. See response format here |
| diarization | object \| null | Yes |  |
| use_separate_streams_when_available | boolean | Yes |  |
| provider | object | Yes | Docs: https://www.assemblyai.com/docs/api-reference/transcripts/submit |
| assembly_ai_async | object \| null | Yes |  |
| deepgram_async | object \| null | Yes |  |
| gladia_v1_async | object \| null | Yes |  |
| gladia_v2_async | object \| null | Yes |  |
| rev_async | object \| null | Yes |  |
| speechmatics_async | object \| null | Yes |  |
| assembly_ai_async_chunked | object | No | Docs: https://www.assemblyai.com/docs/api-reference/transcripts/submit |
| assembly_ai_streaming | object | No | Docs: https://www.assemblyai.com/docs/api-reference/streaming/realtime |
| deepgram_streaming | object | No | Docs: https://developers.deepgram.com/reference/streaming |
| gladia_v1_streaming | object | No | Docs: https://docs.gladia.io/reference/live-audio |
| gladia_v2_streaming | object | No | Docs: https://docs.gladia.io/api-reference/v2/live/init |
| rev_streaming | object | No | Docs: https://docs.rev.ai/api/streaming/requests/ |
| aws_transcribe_streaming | object | No | You must specify either:  language_code(e.g en-US) OR Set language_identification to true AND specify language_options(e.g en-US,fr-FR,es-US,de-DE,it-IT).  Docs: https://docs.aws.amazon.com/transcribe/latest/APIReference/API_streaming_StartStreamTranscription.html |
| speechmatics_streaming | object | No | You must specify language (e.g en) Docs: https://docs.speechmatics.com/rt-api-ref#transcription-config |
| meeting_captions | object | No |  |
