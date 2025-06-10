---
title: "List Google LoginsMoon (Dark Mode)Sun (Light Mode)"
description: "Get list of all Google Logins. This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/google_logins_list.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:58:50.524Z"
api_parameters_count: "14"
---
## GET https://us-east-1.recall.ai/api/v2/google-logins/

Get list of all Google Logins

> **Rate Limiting**: 60 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Signed-In Google Meet Bots](/docs/google-meet-login-getting-started.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| cursor | string | No | The pagination cursor value. |
| email | string | No |  |
| group_id | uuid | No |  |
| is_active | boolean | No |  |
| ordering | string | No | Which field to use when ordering the results. |
| sso_v2_workspace_domain | string | No |  |
| next | string \| null | No |  |
| previous | string \| null | No |  |
| results | array of objects | No | The email address of the google account to use for login. |
| id | uuid | Yes |  |
| sso_v2_private_key | string | Yes | PEM-formatted private key used for signing SSO requests. |
| sso_v2_cert | string | Yes | PEM-formatted x509 certificate which is registered in your Google Workspace SSO Profile. |
| created_at | date-time | Yes |  |
| updated_at | date-time | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/google-logins/"
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
      "email": "user@example.com",
      "is_active": true,
      "sso_v2_workspace_domain": "string",
      "sso_v2_private_key": "string",
      "sso_v2_cert": "string",
      "group_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "created_at": "2025-06-10T18:58:41.882Z",
      "updated_at": "2025-06-10T18:58:41.882Z"
    }
  ]
}
```
