---
title: "Delete Video MixedMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/video_mixed_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:05:31.061Z"
api_parameters_count: "1"
---
## DELETE https://us-east-1.recall.ai/api/v1/video_mixed/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this video mixed artifact. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/video_mixed/id/"
response = requests.delete(url)
print(response.text)
```
