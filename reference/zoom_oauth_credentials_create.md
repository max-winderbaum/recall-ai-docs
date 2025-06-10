---
title: "Create Zoom OAuth CredentialMoon (Dark Mode)Sun (Light Mode)"
description: "Create a new Zoom OAuth Credential. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/zoom_oauth_credentials_create.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:15.371Z"
api_parameters_count: "12"
---
## POST https://us-east-1.recall.ai/api/v2/zoom-oauth-credentials/

Create a new Zoom OAuth Credential

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see:
- [Recall-Managed OAuth](/docs/recall-managed-oauth#calling-the-recall-api.md)
- [Customer Managed OAuth](/docs/customer-managed-oauth#registering-the-callback-url-in-the-recall-api.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| oauth_app | uuid | Yes |  |
| authorization_code | object | No | Data received from Zoom after the user has authorized the app. Applicable for Recall Managed OAuth flow. |
| access_token_callback_url | string \| null | No | The url to retrieve access token from. Applicable for Customer Managed OAuth flow. |
| id | uuid | Yes |  |
| status | string | Yes | healthy - Healthy unhealthy - Unhealthy  healthy unhealthy |
| user_id | string \| null | Yes |  |
| account_id | string \| null | Yes |  |
| created_at | date-time | Yes |  |
| meeting_sync_status | string | Yes | not_started - Not Started in_progress - In Progress completed - Completed failed - Failed  not_started in_progress completed failed |
| detail | string | Yes |  |
| conflicting_zoom_account_id | string | No | The Zoom account ID of the conflicting credential, if any. |
| conflicting_zoom_user_id | string | No | The Zoom user ID of the conflicting credential, if any. |
