---
title: "Delete Meeting MetadataMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/meeting_metadata_destroy.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:59:40.423Z"
api_parameters_count: "1"
---
## DELETE https://us-east-1.recall.ai/api/v1/meeting_metadata/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this meeting metadata artifact. |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/meeting_metadata/id/"
response = requests.delete(url)
print(response.text)
```
