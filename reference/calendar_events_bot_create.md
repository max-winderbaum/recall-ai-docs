---
title: "Schedule Bot For Calendar EventMoon (Dark Mode)Sun (Light Mode)"
description: "Schedule a bot for a calendar event. This endpoint will return the updated calendar event in response. This endpoint is rate limited to: 600 requests per min per workspace"
source_file: "reference/calendar_events_bot_create.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:13.177Z"
api_parameters_count: "17"
---
## POST https://us-east-1.recall.ai/api/v2/calendar-events/{id}/bot/

Schedule a bot for a calendar event. This endpoint will return the updated calendar event in response

> **Rate Limiting**: 600 requests per min per workspace

**For more information, see [Calendar V2](/docs/v2.md).**

> **CALLOUT**:

## 📘

Override behavior

When calling this endpoint for an event that already has a bot scheduled, the existing bot configuration will be overridden with the new settings provided in the request.

> **CALLOUT**:

## 🚧

Meeting URL response shape

Meeting URL's are currently improperly reflected in the API spec for **meeting URL's in responses**. For proper meeting URL shapes in API responses, please see [Meeting URL's](/docs/meeting-urls.md).

`meeting_url`'s that are provided as a **parameter** to the API are reflected accurately in the API spec as strings.



### Scheduling error response

[](#scheduling-error-response)

If you try to schedule a bot for an event that has already ended, you'll receive a 400 response:

JSON

```
{
  "code": "invalid_request_data",
  "message": "Unable to process request because invalid data was submitted. Check `errors` field for more details.",
  "errors": {
    "non_field_errors": [
      "Cannot schedule bot as calendar event has ended."
    ]
  }
}

```
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this calendar event. |
| deduplication_key | string | Yes | Pass this key to deduplicate bots across multiple calendar events. Please ensure this remain consistent across all calendar events that mush share a single bot. For more details, refer to Calendar V2 scheduling guide. |
| bot_config | object | Yes | The config object(JSON) to be passed to the bot. It supports all properties available in Create Bot request.  meeting_url - automatically populated from the calendar event unless specified in bot_config. join_at - automatically populated from the calendar event unless specified in bot_config |
| start_time | date-time | Yes |  |
| end_time | date-time | Yes |  |
| calendar_id | uuid | Yes |  |
| raw | string | Yes |  |
| platform | string | Yes |  |
| platform_id | string | Yes |  |
| ical_uid | string | Yes |  |
| meeting_platform | string | Yes |  |
| meeting_url | string \| null | Yes |  |
| created_at | date-time | Yes |  |
| updated_at | date-time | Yes |  |
| is_deleted | boolean | Yes |  |
| bots | array of objects | Yes |  |
| bot_id | uuid | Yes |  |
