---
title: "Delete Participant EventsMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/participant_events_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:00:24.391Z"
api_parameters_count: "1"
---
## DELETE https://us-east-1.recall.ai/api/v1/participant_events/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this participant events artifact. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/participant_events/id/"
response = requests.delete(url)
print(response.text)
```
