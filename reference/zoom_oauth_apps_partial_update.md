---
title: "Update Zoom OAuth AppMoon (Dark Mode)Sun (Light Mode)"
description: "Update an existing Zoom OAuth App This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/zoom_oauth_apps_partial_update.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:08:22.613Z"
api_parameters_count: "7"
---
## PATCH https://us-east-1.recall.ai/api/v2/zoom-oauth-apps/{id}/

Update an existing Zoom OAuth App This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this zoom o auth app. |
| webhook_secret | string | No |  |
| client_secret | string | No |  |
| kind | string | Yes | user_level - User Level account_level - Account Level  user_level account_level |
| client_id | string | Yes |  |
| webhook_last_validation | date-time \| null | Yes |  |
| created_at | date-time | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/zoom-oauth-apps/id/"
payload = {
"webhook_secret": "string",
"client_secret": "string"
}
headers = {
"accept": "application/json",
"content-type": "application/json"
}
response = requests.patch(url, json = payload, headers = headers)
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
  "webhook_last_validation": "2025-06-10T19:08:11.929Z",
  "created_at": "2025-06-10T19:08:11.929Z"
}
```
