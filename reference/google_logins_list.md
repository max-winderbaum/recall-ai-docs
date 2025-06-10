---
title: "List Google LoginsMoon (Dark Mode)Sun (Light Mode)"
description: "Get list of all Google Logins. This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/google_logins_list.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:13.872Z"
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
