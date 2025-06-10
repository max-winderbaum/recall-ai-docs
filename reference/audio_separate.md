---
title: "List Audio SeparateMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/audio_separate.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:12.514Z"
api_parameters_count: "15"
---
## GET https://us-east-1.recall.ai/api/v1/audio_separate/

This endpoint is rate limited to: 60 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| created_at_after | date-time | No |  |
| created_at_before | date-time | No |  |
| cursor | string | No | The pagination cursor value. |
| recording_id | uuid | No |  |
| status_code | string | No | processing - Processing done - Done failed - Failed |
| next | string \| null | No |  |
| previous | string \| null | No |  |
| results | array of objects | No | raw - Raw  raw |
| id | uuid | Yes |  |
| recording | object | Yes |  |
| created_at | date-time | Yes |  |
| status | object | Yes |  |
| metadata | object | Yes |  |
| data | object | Yes |  |
| format | string | Yes | raw - Raw  raw |
