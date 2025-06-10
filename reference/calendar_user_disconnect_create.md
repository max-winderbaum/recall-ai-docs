---
title: "Disconnect Calendar PlatformMoon (Dark Mode)Sun (Light Mode)"
description: "Disconnect calendar of specific platform. This endpoint is rate limited to: 120 requests per min per calendar_user"
source_file: "reference/calendar_user_disconnect_create.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:55:41.056Z"
api_parameters_count: "14"
---
## POST https://us-east-1.recall.ai/api/v1/calendar/user/disconnect/

Disconnect calendar of specific platform

> **Rate Limiting**: 120 requests per min per calendar_user

> **CALLOUT**:

## 📘

For more information, see [Calendar V1](/docs/calendar-v1-1.md).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| platform | string | Yes | google - Google microsoft - Microsoft |
| id | uuid | Yes |  |
| external_id | string | No |  |
| connections | array of objects | Yes |  |
| connected | boolean | Yes |  |
| email | string | No |  |
| preferences | object | No |  |
| record_non_host | boolean | No |  |
| record_recurring | boolean | No |  |
| record_external | boolean | No |  |
| record_internal | boolean | No |  |
| record_confirmed | boolean | No |  |
| record_only_host | boolean | No |  |
| bot_name | string | No |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/calendar/user/disconnect/"
payload = { "platform": "google" }
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
  "external_id": "string",
  "connections": [
    {
      "connected": true,
      "platform": "string",
      "email": "string",
      "id": "string"
    }
  ],
  "preferences": {
    "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "record_non_host": true,
    "record_recurring": true,
    "record_external": true,
    "record_internal": true,
    "record_confirmed": true,
    "record_only_host": true,
    "bot_name": "string"
  }
}
```
