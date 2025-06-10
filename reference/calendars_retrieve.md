---
title: "Retrieve CalendarMoon (Dark Mode)Sun (Light Mode)"
description: "Get a calendar instance. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/calendars_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:14.001Z"
api_parameters_count: "12"
---
## GET https://us-east-1.recall.ai/api/v2/calendars/{id}/

Get a calendar instance

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Calendar V2](/docs/v2).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this calendar. |
| oauth_client_id | string | Yes |  |
| oauth_client_secret | string | Yes |  |
| oauth_refresh_token | string | Yes |  |
| platform | string | Yes | google_calendar - Google Calendar microsoft_outlook - Microsoft Outlook  google_calendar microsoft_outlook |
| webhook_url | uri | No |  |
| oauth_email | string | No |  |
| platform_email | string \| null | Yes |  |
| status | string | Yes |  |
| status_changes | string | Yes |  |
| created_at | date-time | Yes |  |
| updated_at | date-time | Yes |  |
