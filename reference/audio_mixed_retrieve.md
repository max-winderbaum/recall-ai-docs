---
title: "Retrieve Audio MixedMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/audio_mixed_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T18:48:01.268Z"
api_parameters_count: "11"
---
## GET https://us-east-1.recall.ai/api/v1/audio_mixed/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this audio mixed artifact. |
| recording | object | Yes |  |
| metadata | object \| null | Yes |  |
| created_at | date-time | Yes |  |
| status | object | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| code | string | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| sub_code | string \| null | Yes |  |
| updated_at | date-time | Yes |  |
| data | object | Yes |  |
| download_url | uri \| null | Yes |  |
| format | string | Yes | raw - Raw  raw |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/audio_mixed/id/"
headers = {"accept": "application/json"}
response = requests.get(url, headers = headers)
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
  "created_at": "2025-06-10T18:47:52.637Z",
  "status": {
    "code": "processing",
    "sub_code": "string",
    "updated_at": "2025-06-10T18:47:52.637Z"
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
