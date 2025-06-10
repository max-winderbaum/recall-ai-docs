---
title: "Retrieve Calendar EventMoon (Dark Mode)Sun (Light Mode)"
description: "Get a calendar event instance. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/calendar_events_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:54:45.438Z"
api_parameters_count: "16"
---
## GET https://us-east-1.recall.ai/api/v2/calendar-events/{id}/

Get a calendar event instance

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Calendar V2](/docs/v2.md).

## `raw` field

[](#raw-field)

Examples of the platform-specific `raw` field data can be found at [Calendar Event Platform Data](/reference/calendar-event-platform-data.md).
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
url = "https://us-east-1.recall.ai/api/v2/calendar-events/id/"
headers = {"accept": "application/json"}
response = requests.get(url, headers = headers)
print(response.text)
```

## Sample Response

```json
{
  "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "start_time": "2025-06-10T18:54:36.868Z",
  "end_time": "2025-06-10T18:54:36.868Z",
  "calendar_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "platform": "string",
  "platform_id": "string",
  "ical_uid": "string",
  "meeting_platform": "zoom",
  "meeting_url": "string",
  "created_at": "2025-06-10T18:54:36.868Z",
  "updated_at": "2025-06-10T18:54:36.868Z",
  "is_deleted": true,
  "bots": [
    {
      "bot_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "start_time": "2025-06-10T18:54:36.868Z",
      "deduplication_key": "string",
      "meeting_url": "string"
    }
  ]
}
```
