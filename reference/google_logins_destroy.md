---
title: "Destroy Google LoginMoon (Dark Mode)Sun (Light Mode)"
description: "Deletes an existing Google Login. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/google_logins_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:13.848Z"
api_parameters_count: "1"
---
## DELETE https://us-east-1.recall.ai/api/v2/google-logins/{id}/

Deletes an existing Google Login

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Signed-In Google Meet Bots](/docs/google-meet-login-getting-started.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this google login. |
