---
title: "List Realtime EndpointsMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/realtime_endpoint.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:14.645Z"
api_parameters_count: "16"
---
## GET https://us-east-1.recall.ai/api/v1/realtime_endpoint/

This endpoint is rate limited to: 60 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| created_at_after | date-time | No |  |
| created_at_before | date-time | No |  |
| cursor | string | No | The pagination cursor value. |
| recording_id | uuid | No |  |
| status_code | string | No | running - Running done - Done failed - Failed |
| type | string | No | rtmp - Rtmp websocket - Websocket webhook - Webhook desktop-sdk-callback - Desktop Sdk Callback |
| next | string \| null | No |  |
| previous | string \| null | No |  |
| results | array of objects | No |  |
| id | uuid | Yes |  |
| created_at | date-time | Yes |  |
| recording | object | Yes |  |
| metadata | object | Yes |  |
| status | object | Yes |  |
| url | uri | Yes |  |
| events | array of strings | Yes |  |
