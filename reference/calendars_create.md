---
title: "Create CalendarMoon (Dark Mode)Sun (Light Mode)"
description: "Create a new calendar. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/calendars_create.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:13.917Z"
api_parameters_count: "12"
---
## POST https://us-east-1.recall.ai/api/v2/calendars/

Create a new calendar

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Calendar V2](/docs/v2).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| oauth_client_id | string | Yes |  |
| oauth_client_secret | string | Yes |  |
| oauth_refresh_token | string | Yes |  |
| platform | string | Yes | google_calendar - Google Calendar microsoft_outlook - Microsoft Outlook |
| oauth_email | string | No |  |
| id | uuid | Yes |  |
| webhook_url | uri | No |  |
| platform_email | string \| null | Yes |  |
| status | string | Yes |  |
| status_changes | string | Yes |  |
| created_at | date-time | Yes |  |
| updated_at | date-time | Yes |  |
