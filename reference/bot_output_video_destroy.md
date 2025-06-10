---
title: "Output VideoMoon (Dark Mode)Sun (Light Mode)"
description: "Causes the bot to start outputting video. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/bot_output_video_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:13.098Z"
api_parameters_count: "1"
---
## POST https://us-east-1.recall.ai/api/v1/bot/{id}/output_video/

Causes the bot to start outputting video

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Output an Image](/docs/output-video-in-meetings).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this bot. |
