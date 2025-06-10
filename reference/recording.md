---
title: "List RecordingsMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/recording.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:14.309Z"
api_parameters_count: "20"
---
## GET https://us-east-1.recall.ai/api/v1/recording/

This endpoint is rate limited to: 60 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| bot_id | uuid | No |  |
| created_at_after | date-time | No |  |
| created_at_before | date-time | No |  |
| cursor | string | No | The pagination cursor value. |
| desktop_sdk_upload_id | uuid | No |  |
| status_code | string \| null | No | processing - Processing paused - Paused done - Done failed - Failed |
| next | string \| null | No |  |
| previous | string \| null | No |  |
| results | array of objects | No |  |
| id | uuid | Yes |  |
| created_at | date-time | Yes |  |
| started_at | date-time \| null | Yes |  |
| completed_at | date-time \| null | Yes |  |
| status | object | Yes |  |
| media_shortcuts | object | Yes |  |
| realtime_endpoints | array of objects | Yes |  |
| metadata | object | Yes |  |
| bot | object \| null | Yes |  |
| desktop_sdk_upload | object \| null | Yes |  |
| expires_at | date-time | Yes |  |
