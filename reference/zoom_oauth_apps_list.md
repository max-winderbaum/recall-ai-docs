---
title: "List Zoom OAuth AppsMoon (Dark Mode)Sun (Light Mode)"
description: "Get a list of all Zoom OAuth Apps. This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/zoom_oauth_apps_list.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:08:11.231Z"
api_parameters_count: "16"
---
## GET https://us-east-1.recall.ai/api/v2/zoom-oauth-apps/

Get a list of all Zoom OAuth Apps

> **Rate Limiting**: 60 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Zoom OAuth Integration](/docs/zoom-oauth-integration.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| client_id | string | No |  |
| created_at_after | date-time | No |  |
| created_at_before | date-time | No |  |
| cursor | string | No | The pagination cursor value. |
| kind | string | No |  |
| ordering | string | No | Which field to use when ordering the results. |
| webhook_last_validation_after | date-time | No |  |
| webhook_last_validation_before | date-time | No |  |
| next | string \| null | No |  |
| previous | string \| null | No |  |
| results | array of objects | No | user_level - User Level account_level - Account Level  user_level account_level |
| id | uuid | Yes |  |
| client_secret | string | Yes |  |
| webhook_secret | string | Yes |  |
| webhook_last_validation | date-time \| null | Yes |  |
| created_at | date-time | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/zoom-oauth-apps/"
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
      "kind": "user_level",
      "client_id": "string",
      "client_secret": "string",
      "webhook_secret": "string",
      "webhook_last_validation": "2025-06-10T19:08:02.579Z",
      "created_at": "2025-06-10T19:08:02.579Z"
    }
  ]
}
```
