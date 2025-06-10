---
title: "List Calendar EventsMoon (Dark Mode)Sun (Light Mode)"
description: "Get a list of calendar events. This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/calendar_events_list.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:13.652Z"
api_parameters_count: "23"
---
## GET https://us-east-1.recall.ai/api/v2/calendar-events/

Get a list of calendar events

> **Rate Limiting**: 60 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Calendar V2](/docs/v2).

## `raw` field

[](#raw-field)

Examples of the platform-specific `raw` field data can be found at [Calendar Event Platform Data](/reference/calendar-event-platform-data).

A maximum of 100 events are returned. If more events exist, the response will include a `next` string with the full URL and cursor to retrieve the next page of paginated results.

Example:

json

```
{
  "next": "https://us-east-1.recall.ai/api/v2/calendar-events/?cursor=cD0yMDI0LTAyLTIyKzE2JTNBMTUlM0EwMCUyQjAwJTNBMDA%3D",
  "previous": null,
  "results": [...], // 100 events
}

```
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| calendar_id | uuid | No |  |
| cursor | string | No | The pagination cursor value. |
| ical_uid | string | No | Filter results by ical_uid. (Case sensitive prefix match will be performed.) |
| is_deleted | boolean | No |  |
| start_time | date-time | No |  |
| start_time__gte | date-time | No |  |
| start_time__lte | date-time | No |  |
| updated_at__gte | date-time | No |  |
| next | string \| null | No |  |
| previous | string \| null | No |  |
| results | array of objects | No |  |
| id | uuid | Yes |  |
| end_time | date-time | Yes |  |
| raw | string | Yes |  |
| platform | string | Yes |  |
| platform_id | string | Yes |  |
| meeting_platform | string | Yes |  |
| meeting_url | string \| null | Yes |  |
| created_at | date-time | Yes |  |
| updated_at | date-time | Yes |  |
| bots | array of objects | Yes |  |
| bot_id | uuid | Yes |  |
| deduplication_key | string | Yes |  |
