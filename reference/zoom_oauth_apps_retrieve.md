---
title: "Retrieve Zoom OAuth AppMoon (Dark Mode)Sun (Light Mode)"
description: "Get a Zoom OAuth App. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/zoom_oauth_apps_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:08:31.814Z"
api_parameters_count: "7"
---
## GET https://us-east-1.recall.ai/api/v2/zoom-oauth-apps/{id}/

Get a Zoom OAuth App

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Zoom OAuth Integration](/docs/zoom-oauth-integration.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this zoom o auth app. |
| kind | string | Yes | user_level - User Level account_level - Account Level  user_level account_level |
| client_id | string | Yes |  |
| client_secret | string | Yes |  |
| webhook_secret | string | Yes |  |
| webhook_last_validation | date-time \| null | Yes |  |
| created_at | date-time | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/zoom-oauth-apps/id/"
headers = {"accept": "application/json"}
response = requests.get(url, headers = headers)
print(response.text)
```

## Sample Response

```json
{
  "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "kind": "user_level",
  "client_id": "string",
  "client_secret": "string",
  "webhook_secret": "string",
  "webhook_last_validation": "2025-06-10T19:08:23.187Z",
  "created_at": "2025-06-10T19:08:23.187Z"
}
```
