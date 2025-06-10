---
title: "Update Audio SeparateMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/audio_separate_partial_update.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:48:36.153Z"
api_parameters_count: "11"
---
## PATCH https://us-east-1.recall.ai/api/v1/audio_separate/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this audio separate artifact. |
| metadata | object | No |  |
| recording | object | Yes |  |
| created_at | date-time | Yes |  |
| status | object | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| code | string | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| sub_code | string \| null | Yes |  |
| updated_at | date-time | Yes |  |
| data | object | Yes | Download all audio separate parts for the recording. See response format here |
| download_url | uri \| null | Yes | Download all audio separate parts for the recording. See response format here |
| format | string | Yes | raw - Raw  raw |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/audio_separate/id/"
payload = { "metadata": { "additionalProp": "string" } }
headers = {
"accept": "application/json",
"content-type": "application/json"
}
response = requests.patch(url, json = payload, headers = headers)
print(response.text)
```

## Sample Response

```json
{
  "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "recording": {
    "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "metadata": {
      "additionalProp": "string"
    }
  },
  "created_at": "2025-06-10T18:48:25.458Z",
  "status": {
    "code": "processing",
    "sub_code": "string",
    "updated_at": "2025-06-10T18:48:25.458Z"
  },
  "metadata": {
    "additionalProp": "string"
  },
  "data": {
    "download_url": "string"
  },
  "format": "raw"
}
```
