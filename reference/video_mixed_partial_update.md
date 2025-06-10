---
title: "Update Video MixedMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/video_mixed_partial_update.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:05:51.262Z"
api_parameters_count: "11"
---
## PATCH https://us-east-1.recall.ai/api/v1/video_mixed/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this video mixed artifact. |
| metadata | object | No |  |
| recording | object | Yes |  |
| created_at | date-time | Yes |  |
| status | object | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| code | string | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| sub_code | string \| null | Yes |  |
| updated_at | date-time | Yes |  |
| data | object | Yes |  |
| download_url | uri \| null | Yes |  |
| format | string | Yes | mp4 - Mp4  mp4 |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/video_mixed/id/"
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
  "created_at": "2025-06-10T19:05:40.485Z",
  "status": {
    "code": "processing",
    "sub_code": "string",
    "updated_at": "2025-06-10T19:05:40.485Z"
  },
  "metadata": {
    "additionalProp": "string"
  },
  "data": {
    "download_url": "string"
  },
  "format": "mp4"
}
```
