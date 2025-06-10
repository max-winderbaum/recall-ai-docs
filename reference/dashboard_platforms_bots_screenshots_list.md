---
title: "List Bot ScreenshotsMoon (Dark Mode)Sun (Light Mode)"
description: "Get a list of all screenshots of the bot This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/dashboard_platforms_bots_screenshots_list.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:14.022Z"
api_parameters_count: "9"
---
## GET https://us-east-1.recall.ai/dashboard/platforms/bots/{bot_id}/screenshots/

Get a list of all screenshots of the bot This endpoint is rate limited to: 60 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| bot_id | uuid | Yes | The ID of the bot for which to retrieve the screenshots |
| action | string | No | Navigation direction ('prev' for previous page) |
| continuation_token | string | No | Token for fetching the next page of results |
| meta | string | No | Encoded metadata for pagination state |
| recorded_at_after | date-time | No | Filter screenshots recorded after this datetime |
| recorded_at_before | date-time | No | Filter screenshots recorded before this datetime |
| id | string | Yes |  |
| recorded_at | date-time | Yes |  |
| url | uri | Yes |  |
