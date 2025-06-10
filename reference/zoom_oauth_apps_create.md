---
title: "Create Zoom OAuth AppMoon (Dark Mode)Sun (Light Mode)"
description: "Create a new Zoom OAuth App. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/zoom_oauth_apps_create.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:15.684Z"
api_parameters_count: "7"
---
## POST https://us-east-1.recall.ai/api/v2/zoom-oauth-apps/

Create a new Zoom OAuth App

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Zoom OAuth Integration](/docs/zoom-oauth-integration)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| kind | string | Yes | user_level - User Level account_level - Account Level |
| client_id | string | Yes |  |
| client_secret | string | Yes |  |
| webhook_secret | string | Yes |  |
| id | uuid | Yes |  |
| webhook_last_validation | date-time \| null | Yes |  |
| created_at | date-time | Yes |  |
