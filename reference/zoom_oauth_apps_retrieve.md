---
title: "Retrieve Zoom OAuth AppMoon (Dark Mode)Sun (Light Mode)"
description: "Get a Zoom OAuth App. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/zoom_oauth_apps_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:15.767Z"
api_parameters_count: "7"
---
## GET https://us-east-1.recall.ai/api/v2/zoom-oauth-apps/{id}/

Get a Zoom OAuth App

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Zoom OAuth Integration](/docs/zoom-oauth-integration)
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
