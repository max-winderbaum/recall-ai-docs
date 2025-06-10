---
title: "Delete CalendarMoon (Dark Mode)Sun (Light Mode)"
description: "Deletes a calendar. This will disconnect the calendar. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/calendars_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:56:27.072Z"
api_parameters_count: "1"
---
## DELETE https://us-east-1.recall.ai/api/v2/calendars/{id}/

Deletes a calendar. This will disconnect the calendar

> **Rate Limiting**: 300 requests per min per workspace

> **CALLOUT**:

## 📘

For more information, see [Calendar V2](/docs/v2.md).
## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this calendar. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v2/calendars/id/"
response = requests.delete(url)
print(response.text)
```
