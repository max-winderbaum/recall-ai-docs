---
title: "Output AudioMoon (Dark Mode)Sun (Light Mode)"
description: "Causes the bot to output audio. Note: The bot must be configured with 'automatic_audio_output' enabled in order to use this endpoint. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/bot_output_audio_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:12.520Z"
api_parameters_count: "1"
---
## POST https://us-east-1.recall.ai/api/v1/bot/{id}/output_audio/

Causes the bot to output audio. Note: The bot must be configured with 'automatic_audio_output' enabled in order to use this endpoint

> **Rate Limiting**: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this bot. |
