---
title: "Get Calendar Auth TokenMoon (Dark Mode)Sun (Light Mode)"
description: "Generate an authentication token for calendar APIs, scoped to the user. Each token has an expiry of 1 day from time of creation. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/calendar_authenticate_create.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:54:07.271Z"
api_parameters_count: "2"
---
## GET https://us-east-1.recall.ai/api/v1/calendar/authenticate/

Generate an authentication token for calendar APIs, scoped to the user. Each token has an expiry of 1 day from time of creation

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

If a calendar user with the provided `external_id` doesn't exist, it will be created.

For more information, see [Calendar V1](/docs/calendar-v1-1#generate-a-calendar-auth-token.md).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| user_id | string | Yes | The unique id of the user in your system. |
| token | string | Yes | The authentication token for the user. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/calendar/authenticate/"
payload = { "user_id": "string" }
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
  "token": "string"
}
```
