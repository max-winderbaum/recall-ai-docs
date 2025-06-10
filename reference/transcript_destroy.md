---
title: "Delete TranscriptMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/transcript_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:04:46.712Z"
api_parameters_count: "1"
---
## DELETE https://us-east-1.recall.ai/api/v1/transcript/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this transcript artifact. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/transcript/id/"
response = requests.delete(url)
print(response.text)
```
