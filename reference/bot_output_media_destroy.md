---
title: "Output MediaMoon (Dark Mode)Sun (Light Mode)"
description: "Causes the bot to start outputting media. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/bot_output_media_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:12.998Z"
api_parameters_count: "3"
---
## POST https://us-east-1.recall.ai/api/v1/bot/{id}/output_media/

Causes the bot to start outputting media

> **Rate Limiting**: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this bot. |
| camera | boolean | No | Stop outputting media on the bot camera |
| screenshare | boolean | No | Stop outputting media on the bot screenshare |
