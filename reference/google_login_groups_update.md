---
title: "Update Google Login GroupMoon (Dark Mode)Sun (Light Mode)"
description: "Update an existing Google Login Group. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/google_login_groups_update.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:13.786Z"
api_parameters_count: "12"
---
## PATCH https://us-east-1.recall.ai/api/v2/google-login-groups/{id}/

Update an existing Google Login Group

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Signed-In Google Meet Bots](/docs/google-meet-login-getting-started.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this google login group. |
| name | string | Yes | Name of the login group. It can used to filter out login groups when retrieving them via API. |
| login_mode | string | Yes | always - Always only_if_required - Only If Required |
| created_at | date-time | Yes |  |
| updated_at | date-time | Yes |  |
| logins | array of objects | Yes | The email address of the google account to use for login. |
| email | string | Yes | The email address of the google account to use for login. |
| is_active | boolean | No | If the login should be used for round robin. (default: true) |
| sso_v2_workspace_domain | string | Yes | The primary domain name of your Google Workspace Account used for SSO. |
| sso_v2_private_key | string | Yes | PEM-formatted private key used for signing SSO requests. |
| sso_v2_cert | string | Yes | PEM-formatted x509 certificate which is registered in your Google Workspace SSO Profile. |
| group_id | uuid | Yes | The id of the login group this login belongs to. |
