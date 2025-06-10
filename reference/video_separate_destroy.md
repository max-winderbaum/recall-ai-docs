---
title: "Delete Video SeparateMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/video_separate_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:06:15.080Z"
api_parameters_count: "1"
---
## DELETE https://us-east-1.recall.ai/api/v1/video_separate/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this video separate artifact. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/video_separate/id/"
response = requests.delete(url)
print(response.text)
```
