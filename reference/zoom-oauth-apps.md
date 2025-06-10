---
title: "List Zoom OAuth App LogsMoon (Dark Mode)Sun (Light Mode)"
description: "Get a list of all Zoom OAuth App Logs. Any warnings or errors related to the OAuth App will be logged here, and this can be helpful for debugging. This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/zoom-oauth-apps.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:15.103Z"
api_parameters_count: "10"
---
## GET https://us-east-1.recall.ai/api/v2/zoom-oauth-app-logs/

Get a list of all Zoom OAuth App Logs. Any warnings or errors related to the OAuth App will be logged here, and this can be helpful for debugging

> **Rate Limiting**: 60 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Zoom OAuth Integration](/docs/zoom-oauth-integration.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| created_at_after | date-time | No |  |
| created_at_before | date-time | No |  |
| cursor | string | No | The pagination cursor value. |
| oauth_app | uuid | No |  |
| ordering | string | No | Which field to use when ordering the results. |
| next | string \| null | No |  |
| previous | string \| null | No |  |
| results | array of objects | No |  |
| message | string | Yes |  |
| created_at | date-time | Yes |  |
