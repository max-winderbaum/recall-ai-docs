---
title: "/api/v2/calendar-accounts/{uuid}/Moon (Dark Mode)Sun (Light Mode)"
description: "Recall.ai is the universal API for meeting bots."
source_file: "reference/calendar-accounts.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:53:13.838Z"
api_parameters_count: "4"
---
## GET https://us-east-1.recall.ai/api/v2/calendar-accounts/{uuid}/

Recall.ai is the universal API for meeting bots.

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| uuid | string | Yes |  |
| id | uuid | Yes |  |
| platform | string | Yes |  |
| email | string | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/calendar-accounts/uuid/"
headers = {"accept": "application/json"}
response = requests.get(url, headers = headers)
print(response.text)
```

## Sample Response

```json
{
  "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "platform": "string",
  "email": "user@example.com"
}
```
