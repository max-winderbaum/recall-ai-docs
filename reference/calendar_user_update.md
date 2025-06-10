---
title: "Update Recording PreferencesMoon (Dark Mode)Sun (Light Mode)"
description: "Update the recording preferences for a calendar user. This endpoint is rate limited to: 120 requests per min per calendar_user"
source_file: "reference/calendar_user_update.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:47:13.437Z"
api_parameters_count: "14"
---
## PATCH https://us-east-1.recall.ai/api/v1/calendar/user/

Update the recording preferences for a calendar user

> **Rate Limiting**: 120 requests per min per calendar_user

> **CALLOUT**:

## 📘

For more information, see [Calendar Recording Preferences](/docs/calendar-v1-recording-preferences#recording-preferences.md)
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| external_id | string | No |  |
| preferences | object | No |  |
| id | uuid | Yes |  |
| connections | array of objects | Yes |  |
| connected | boolean | Yes |  |
| platform | string | Yes |  |
| email | string | No |  |
| record_non_host | boolean | No |  |
| record_recurring | boolean | No |  |
| record_external | boolean | No |  |
| record_internal | boolean | No |  |
| record_confirmed | boolean | No |  |
| record_only_host | boolean | No |  |
| bot_name | string | No |  |
