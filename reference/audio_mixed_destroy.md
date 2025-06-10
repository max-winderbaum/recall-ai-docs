---
title: "Delete Audio MixedMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/audio_mixed_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:47:32.035Z"
api_parameters_count: "1"
---
## DELETE https://us-east-1.recall.ai/api/v1/audio_mixed/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this audio mixed artifact. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/audio_mixed/id/"
response = requests.delete(url)
print(response.text)
```
