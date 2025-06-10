---
title: "List Calendar UsersMoon (Dark Mode)Sun (Light Mode)"
description: "List all calendar users created for the account. This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/calendar_users_list.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:56:10.489Z"
api_parameters_count: "8"
---
## GET https://us-east-1.recall.ai/api/v1/calendar/users/

List all calendar users created for the account

> **Rate Limiting**: 60 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Calendar V1](/docs/calendar-v1-1.md).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| email | string | No | Filter results by email address |
| paginate | boolean | No | Enable pagination for the results |
| id | uuid | Yes |  |
| external_id | string | No |  |
| connections | array of objects | Yes |  |
| connected | boolean | Yes |  |
| platform | string | Yes |  |
| preferences | object | No |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/calendar/users/"
headers = {"accept": "application/json"}
response = requests.get(url, headers = headers)
print(response.text)
```

## Sample Response

```json
[
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
]
```
