---
title: "Retrieve CalendarMoon (Dark Mode)Sun (Light Mode)"
description: "Get a calendar instance. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/calendars_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:56:56.488Z"
api_parameters_count: "12"
---
## GET https://us-east-1.recall.ai/api/v2/calendars/{id}/

Get a calendar instance

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Calendar V2](/docs/v2.md).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this calendar. |
| oauth_client_id | string | Yes |  |
| oauth_client_secret | string | Yes |  |
| oauth_refresh_token | string | Yes |  |
| platform | string | Yes | google_calendar - Google Calendar microsoft_outlook - Microsoft Outlook  google_calendar microsoft_outlook |
| webhook_url | uri | No |  |
| oauth_email | string | No |  |
| platform_email | string \| null | Yes |  |
| status | string | Yes |  |
| status_changes | string | Yes |  |
| created_at | date-time | Yes |  |
| updated_at | date-time | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/calendars/id/"
headers = {"accept": "application/json"}
response = requests.get(url, headers = headers)
print(response.text)
```

## Sample Response

```json
{
  "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "oauth_client_id": "string",
  "oauth_client_secret": "string",
  "oauth_refresh_token": "string",
  "platform": "google_calendar",
  "oauth_email": "user@example.com",
  "platform_email": "string",
  "status": "string",
  "created_at": "2025-06-10T18:56:47.884Z",
  "updated_at": "2025-06-10T18:56:47.884Z"
}
```
