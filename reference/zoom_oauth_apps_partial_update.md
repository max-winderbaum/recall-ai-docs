---
title: "Update Zoom OAuth AppMoon (Dark Mode)Sun (Light Mode)"
description: "Update an existing Zoom OAuth App This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/zoom_oauth_apps_partial_update.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:15.287Z"
api_parameters_count: "7"
---
## PATCH https://us-east-1.recall.ai/api/v2/zoom-oauth-apps/{id}/

Update an existing Zoom OAuth App This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this zoom o auth app. |
| webhook_secret | string | No |  |
| client_secret | string | No |  |
| kind | string | Yes | user_level - User Level account_level - Account Level  user_level account_level |
| client_id | string | Yes |  |
| webhook_last_validation | date-time \| null | Yes |  |
| created_at | date-time | Yes |  |
