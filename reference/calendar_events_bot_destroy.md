---
title: "Schedule Bot For Calendar EventMoon (Dark Mode)Sun (Light Mode)"
description: "Schedule a bot for a calendar event. This endpoint will return the updated calendar event in response. This endpoint is rate limited to: 600 requests per min per workspace"
source_file: "reference/calendar_events_bot_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:54:27.505Z"
api_parameters_count: "16"
---
## POST https://us-east-1.recall.ai/api/v2/calendar-events/{id}/bot/

Schedule a bot for a calendar event. This endpoint will return the updated calendar event in response

> **Rate Limiting**: 600 requests per min per workspace

For more information, see [Calendar V2 Scheduling Guide](/docs/scheduling-guide#3-addremove-bot-from-the-event.md).


> **CALLOUT**:

## 🔄

This endpoint is idempotent

A request method is considered *idempotent* when executing multiple identical requests with that method yields the same outcome on the server as executing a single request of the same kind.

This means that if the calendar event ID exists, both the first and any following requests will return `200` responses.
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this calendar event. |
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
| deduplication_key | string | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/calendar-events/id/bot/"
headers = {"accept": "application/json"}
response = requests.delete(url, headers = headers)
print(response.text)
```

## Sample Response

```json
{
  "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "start_time": "2025-06-10T18:54:18.951Z",
  "end_time": "2025-06-10T18:54:18.951Z",
  "calendar_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "platform": "string",
  "platform_id": "string",
  "ical_uid": "string",
  "meeting_platform": "zoom",
  "meeting_url": "string",
  "created_at": "2025-06-10T18:54:18.951Z",
  "updated_at": "2025-06-10T18:54:18.951Z",
  "is_deleted": true,
  "bots": [
    {
      "bot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "start_time": "2025-06-10T18:54:18.951Z",
      "deduplication_key": "string",
      "meeting_url": "string"
    }
  ]
}
```
