---
title: "List Desktop SDK UploadsMoon (Dark Mode)Sun (Light Mode)"
description: "Get a list of all Desktop SDK uploads This endpoint is rate limited to: 60 requests per min per workspace"
source_file: "reference/sdk_upload_list.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:03:02.326Z"
api_parameters_count: "6"
---
## GET https://us-east-1.recall.ai/api/v1/sdk-upload/

Get a list of all Desktop SDK uploads This endpoint is rate limited to: 60 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes |  |
| status | object | Yes |  |
| recording_id | string | Yes |  |
| upload_token | string | Yes |  |
| created_at | date-time | Yes |  |
| metadata | object | No |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/sdk-upload/"
headers = {"accept": "application/json"}
response = requests.get(url, headers = headers)
print(response.text)
```

## Sample Response

```json
[
  {
    "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "status": {
      "code": "pending",
      "sub_code": "string",
      "updated_at": "2025-06-10T19:02:53.757Z"
    },
    "recording_id": "string",
    "upload_token": "string",
    "created_at": "2025-06-10T19:02:53.757Z",
    "metadata": {
      "additionalProp": "string"
    }
  }
]
```
