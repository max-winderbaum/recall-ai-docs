---
title: "Update CalendarMoon (Dark Mode)Sun (Light Mode)"
description: "Update an existing calendar. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/calendars_partial_update.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:13.980Z"
api_parameters_count: "12"
---
## PATCH https://us-east-1.recall.ai/api/v2/calendars/{id}/

Update an existing calendar

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Calendar V2](/docs/v2).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this calendar. |
| oauth_client_id | string | No |  |
| oauth_client_secret | string | No |  |
| oauth_refresh_token | string | No |  |
| platform | string | No | google_calendar - Google Calendar microsoft_outlook - Microsoft Outlook |
| oauth_email | string | No |  |
| webhook_url | uri | No |  |
| platform_email | string \| null | Yes |  |
| status | string | Yes |  |
| status_changes | string | Yes |  |
| created_at | date-time | Yes |  |
| updated_at | date-time | Yes |  |
