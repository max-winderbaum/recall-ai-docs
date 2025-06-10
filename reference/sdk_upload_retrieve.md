---
title: "Retrieve Desktop SDK UploadMoon (Dark Mode)Sun (Light Mode)"
description: "Get a Desktop SDK upload instance. This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/sdk_upload_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:03:11.392Z"
api_parameters_count: "9"
---
## GET https://us-east-1.recall.ai/api/v1/sdk-upload/{id}/

Get a Desktop SDK upload instance

> **Rate Limiting**: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | string | Yes |  |
| status | object | Yes | pending - Pending uploading - Uploading complete - Complete failed - Failed  pending uploading complete failed |
| code | string | Yes | pending - Pending uploading - Uploading complete - Complete failed - Failed  pending uploading complete failed |
| sub_code | string \| null | Yes |  |
| updated_at | date-time | Yes |  |
| recording_id | string | Yes |  |
| upload_token | string | Yes |  |
| created_at | date-time | Yes |  |
| metadata | object | No |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/sdk-upload/id/"
headers = {"accept": "application/json"}
response = requests.get(url, headers = headers)
print(response.text)
```

## Sample Response

```json
{
  "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "status": {
    "code": "pending",
    "sub_code": "string",
    "updated_at": "2025-06-10T19:03:02.785Z"
  },
  "recording_id": "string",
  "upload_token": "string",
  "created_at": "2025-06-10T19:03:02.785Z",
  "metadata": {
    "additionalProp": "string"
  }
}
```
