---
title: "Partial Update Google LoginMoon (Dark Mode)Sun (Light Mode)"
description: "Partial Update an existing Google Login. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/google_logins_partial_update.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:59:01.791Z"
api_parameters_count: "9"
---
## PATCH https://us-east-1.recall.ai/api/v2/google-logins/{id}/

Partial Update an existing Google Login

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Signed-In Google Meet Bots](/docs/google-meet-login-getting-started.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this google login. |
| email | string | No | The email address of the google account to use for login. |
| is_active | boolean | No | If the login should be used for round robin. (default: true) |
| sso_v2_workspace_domain | string | No | The primary domain name of your Google Workspace Account used for SSO. |
| sso_v2_private_key | string | No | PEM-formatted private key used for signing SSO requests. |
| sso_v2_cert | string | No | PEM-formatted x509 certificate which is registered in your Google Workspace SSO Profile. |
| group_id | uuid | No | The id of the login group this login belongs to. |
| created_at | date-time | Yes |  |
| updated_at | date-time | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/google-logins/id/"
payload = {
"email": "user@example.com",
"is_active": True,
"sso_v_workspace_domain": "string",
"sso_v_private_key": "string",
"sso_v_cert": "string",
"group_id": "3faf64-57-42-bfc-2cf6afa6"
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
  "email": "user@example.com",
  "is_active": true,
  "sso_v2_workspace_domain": "string",
  "sso_v2_private_key": "string",
  "sso_v2_cert": "string",
  "group_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "created_at": "2025-06-10T18:58:51.087Z",
  "updated_at": "2025-06-10T18:58:51.087Z"
}
```
