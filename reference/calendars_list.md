---
title: "List CalendarsMoon (Dark Mode)Sun (Light Mode)"
description: "Get a list of calendars. This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/calendars_list.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:56:36.124Z"
api_parameters_count: "18"
---
## GET https://us-east-1.recall.ai/api/v2/calendars/

Get a list of calendars

> **Rate Limiting**: 60 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Calendar V2](/docs/v2.md).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| created_at__gte | date-time | No |  |
| cursor | string | No | The pagination cursor value. |
| email | string | No |  |
| platform | string | No | google_calendar - Google Calendar microsoft_outlook - Microsoft Outlook |
| status | string | No | connecting - Connecting connected - Connected disconnected - Disconnected |
| next | string \| null | No |  |
| previous | string \| null | No |  |
| results | array of objects | No | google_calendar - Google Calendar microsoft_outlook - Microsoft Outlook  google_calendar microsoft_outlook |
| id | uuid | Yes |  |
| oauth_client_id | string | Yes |  |
| oauth_client_secret | string | Yes |  |
| oauth_refresh_token | string | Yes |  |
| webhook_url | uri | No |  |
| oauth_email | string | No |  |
| platform_email | string \| null | Yes |  |
| status_changes | string | Yes |  |
| created_at | date-time | Yes |  |
| updated_at | date-time | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/calendars/"
headers = {"accept": "application/json"}
response = requests.get(url, headers = headers)
print(response.text)
```

## Sample Response

```json
{
  "next": "string",
  "previous": "string",
  "results": [
    {
      "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "oauth_client_id": "string",
      "oauth_client_secret": "string",
      "oauth_refresh_token": "string",
      "platform": "google_calendar",
      "oauth_email": "user@example.com",
      "platform_email": "string",
      "status": "string",
      "created_at": "2025-06-10T18:56:27.516Z",
      "updated_at": "2025-06-10T18:56:27.516Z"
    }
  ]
}
```
