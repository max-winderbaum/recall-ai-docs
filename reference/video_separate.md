---
title: "List Video SeparateMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/video_separate.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:06:09.660Z"
api_parameters_count: "15"
---
## GET https://us-east-1.recall.ai/api/v1/video_separate/

This endpoint is rate limited to: 60 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| created_at_after | date-time | No |  |
| created_at_before | date-time | No |  |
| cursor | string | No | The pagination cursor value. |
| recording_id | uuid | No |  |
| status_code | string | No | processing - Processing done - Done failed - Failed |
| next | string \| null | No |  |
| previous | string \| null | No |  |
| results | array of objects | No | mp4 - Mp4  mp4 |
| id | uuid | Yes |  |
| recording | object | Yes |  |
| created_at | date-time | Yes |  |
| status | object | Yes |  |
| metadata | object | Yes |  |
| data | object | Yes |  |
| format | string | Yes | mp4 - Mp4  mp4 |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/video_separate/"
headers = {"accept": "application/json"}
response = requests.get(url, headers = headers)
print(response.text)
```

## Sample Response

```json
{
  "next": "string",
  "previous": "string",
  "results": [
    {
      "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
      "recording": {
        "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "metadata": {
          "additionalProp": "string"
        }
      },
      "created_at": "2025-06-10T19:06:01.041Z",
      "status": {
        "code": "processing",
        "sub_code": "string",
        "updated_at": "2025-06-10T19:06:01.041Z"
      },
      "metadata": {
        "additionalProp": "string"
      },
      "data": {
        "download_url": "string"
      },
      "format": "mp4"
    }
  ]
}
```
