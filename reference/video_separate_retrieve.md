---
title: "Retrieve Video SeparateMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/video_separate_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:06:44.013Z"
api_parameters_count: "11"
---
## GET https://us-east-1.recall.ai/api/v1/video_separate/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this video separate artifact. |
| recording | object | Yes |  |
| metadata | object \| null | Yes |  |
| created_at | date-time | Yes |  |
| status | object | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| code | string | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| sub_code | string \| null | Yes |  |
| updated_at | date-time | Yes |  |
| data | object | Yes | Download all video separate parts for the recording. See response format here |
| download_url | uri \| null | Yes | Download all video separate parts for the recording. See response format here |
| format | string | Yes | mp4 - Mp4  mp4 |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/video_separate/id/"
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
  "created_at": "2025-06-10T19:06:35.398Z",
  "status": {
    "code": "processing",
    "sub_code": "string",
    "updated_at": "2025-06-10T19:06:35.398Z"
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
