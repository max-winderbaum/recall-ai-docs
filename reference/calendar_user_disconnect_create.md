---
title: "Disconnect Calendar PlatformMoon (Dark Mode)Sun (Light Mode)"
description: "Disconnect calendar of specific platform. This endpoint is rate limited to: 120 requests per min per calendar_user"
source_file: "reference/calendar_user_disconnect_create.html"
is_api_reference: "true"
converted_at: "2025-06-10T14:00:13.811Z"
api_parameters_count: "14"
---
## POST https://us-east-1.recall.ai/api/v1/calendar/user/disconnect/

Disconnect calendar of specific platform

> **Rate Limiting**: 120 requests per min per calendar_user

> **CALLOUT**:

## 📘

For more information, see [Calendar V1](/docs/calendar-v1-1).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| platform | string | Yes | google - Google microsoft - Microsoft |
| id | uuid | Yes |  |
| external_id | string | No |  |
| connections | array of objects | Yes |  |
| connected | boolean | Yes |  |
| email | string | No |  |
| preferences | object | No |  |
| record_non_host | boolean | No |  |
| record_recurring | boolean | No |  |
| record_external | boolean | No |  |
| record_internal | boolean | No |  |
| record_confirmed | boolean | No |  |
| record_only_host | boolean | No |  |
| bot_name | string | No |  |
