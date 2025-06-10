---
title: "Retrieve Zoom OAuth CredentialMoon (Dark Mode)Sun (Light Mode)"
description: "Get a Zoom OAuth Credential. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/zoom_oauth_credentials_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:15.894Z"
api_parameters_count: "8"
---
## GET https://us-east-1.recall.ai/api/v2/zoom-oauth-credentials/{id}/

Get a Zoom OAuth Credential

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see:
- [Recall-Managed OAuth](/docs/recall-managed-oauth#calling-the-recall-api)
- [Customer Managed OAuth](/docs/customer-managed-oauth#registering-the-callback-url-in-the-recall-api)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this zoom o auth credential. |
| oauth_app | uuid | Yes |  |
| status | string | Yes | healthy - Healthy unhealthy - Unhealthy  healthy unhealthy |
| user_id | string \| null | Yes |  |
| account_id | string \| null | Yes |  |
| access_token_callback_url | string \| null | No | The url to retrieve access token from. Applicable for Customer Managed OAuth flow. |
| created_at | date-time | Yes |  |
| meeting_sync_status | string | Yes | not_started - Not Started in_progress - In Progress completed - Completed failed - Failed  not_started in_progress completed failed |
