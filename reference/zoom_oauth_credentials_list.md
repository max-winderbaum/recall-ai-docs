---
title: "List Zoom OAuth CredentialsMoon (Dark Mode)Sun (Light Mode)"
description: "Get a list of all Zoom OAuth Credentials This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/zoom_oauth_credentials_list.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:09:16.116Z"
api_parameters_count: "15"
---
## GET https://us-east-1.recall.ai/api/v2/zoom-oauth-credentials/

Get a list of all Zoom OAuth Credentials This endpoint is rate limited to: 60 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see:
- [Recall-Managed OAuth](/docs/recall-managed-oauth#calling-the-recall-api.md)
- [Customer Managed OAuth](/docs/customer-managed-oauth#registering-the-callback-url-in-the-recall-api.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| account_id | string | No |  |
| created_at_after | date-time | No |  |
| created_at_before | date-time | No |  |
| cursor | string | No | The pagination cursor value. |
| meeting_sync_status | string | No | This field tracks the status of initial meeting sync on the credential. This operation is processed asynchronously when the credential is created or when the sync meetings endpoint is called.  not_started - Not Started in_progress - In Progress completed - Completed failed - Failed |
| oauth_app | uuid | No |  |
| ordering | string | No | Which field to use when ordering the results. |
| status | string | No | healthy - Healthy unhealthy - Unhealthy |
| user_id | string | No |  |
| next | string \| null | No |  |
| previous | string \| null | No |  |
| results | array of objects | No | healthy - Healthy unhealthy - Unhealthy  healthy unhealthy |
| id | uuid | Yes |  |
| access_token_callback_url | string \| null | No | The url to retrieve access token from. Applicable for Customer Managed OAuth flow. |
| created_at | date-time | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/zoom-oauth-credentials/"
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
      "oauth_app": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "status": "healthy",
      "user_id": "string",
      "account_id": "string",
      "access_token_callback_url": "string",
      "created_at": "2025-06-10T19:09:07.527Z",
      "meeting_sync_status": "not_started"
    }
  ]
}
```
