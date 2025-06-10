---
title: "Create CalendarMoon (Dark Mode)Sun (Light Mode)"
description: "Create a new calendar. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/calendars_create.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:56:21.706Z"
api_parameters_count: "12"
---
## POST https://us-east-1.recall.ai/api/v2/calendars/

Create a new calendar

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Calendar V2](/docs/v2.md).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| oauth_client_id | string | Yes |  |
| oauth_client_secret | string | Yes |  |
| oauth_refresh_token | string | Yes |  |
| platform | string | Yes | google_calendar - Google Calendar microsoft_outlook - Microsoft Outlook |
| oauth_email | string | No |  |
| id | uuid | Yes |  |
| webhook_url | uri | No |  |
| platform_email | string \| null | Yes |  |
| status | string | Yes |  |
| status_changes | string | Yes |  |
| created_at | date-time | Yes |  |
| updated_at | date-time | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/calendars/"
payload = {
"oauth_client_id": "string",
"oauth_client_secret": "string",
"oauth_refresh_token": "string",
"platform": "google_calendar",
"oauth_email": "user@example.com"
}
headers = {
"accept": "application/json",
"content-type": "application/json"
}
response = requests.post(url, json = payload, headers = headers)
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
  "created_at": "2025-06-10T18:56:10.974Z",
  "updated_at": "2025-06-10T18:56:10.974Z"
}
```
