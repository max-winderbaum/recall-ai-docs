---
title: "Update Recording PreferencesMoon (Dark Mode)Sun (Light Mode)"
description: "Update the recording preferences for a calendar user. This endpoint is rate limited to: 120 requests per min per calendar_user"
source_file: "reference/calendar_user_update.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:56:01.456Z"
api_parameters_count: "14"
---
## PATCH https://us-east-1.recall.ai/api/v1/calendar/user/

Update the recording preferences for a calendar user

> **Rate Limiting**: 120 requests per min per calendar_user

> **CALLOUT**:

## 📘

For more information, see [Calendar Recording Preferences](/docs/calendar-v1-recording-preferences#recording-preferences.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| external_id | string | No |  |
| preferences | object | No |  |
| id | uuid | Yes |  |
| connections | array of objects | Yes |  |
| connected | boolean | Yes |  |
| platform | string | Yes |  |
| email | string | No |  |
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
url = "https://us-east-1.recall.ai/api/v1/calendar/user/"
payload = {
"external_id": "string",
"preferences": {
"record_non_host": True,
"record_recurring": True,
"record_external": True,
"record_internal": True,
"record_confirmed": True,
"record_only_host": True,
"bot_name": "string"
}
}
headers = {
"accept": "application/json",
"content-type": "application/json"
}
response = requests.put(url, json = payload, headers = headers)
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
