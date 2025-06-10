---
title: "Retrieve Meeting MetadataMoon (Dark Mode)Sun (Light Mode)"
description: "This endpoint is rate limited to: 300 requests per min per workspace"
source_file: "reference/meeting_metadata_retrieve.html"
is_api_reference: "true"
converted_at: "2025-06-10T19:00:09.691Z"
api_parameters_count: "11"
---
## GET https://us-east-1.recall.ai/api/v1/meeting_metadata/{id}/

This endpoint is rate limited to: 300 requests per min per workspace

## Parameters

| Name | Type | Required | Description |
| --- | --- | --- | --- |
| id | uuid | Yes | A UUID string identifying this meeting metadata artifact. |
| recording | object | Yes |  |
| metadata | object \| null | Yes |  |
| created_at | date-time | Yes |  |
| status | object | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| code | string | Yes | processing - Processing done - Done failed - Failed deleted - Deleted  processing done failed deleted |
| sub_code | string \| null | Yes |  |
| updated_at | date-time | Yes |  |
| data | object | Yes |  |
| title | string \| null | Yes |  |
| zoom | object \| null | Yes |  |

## Python Code Sample

```python
import requests
url = "https://us-east-1.recall.ai/api/v1/meeting_metadata/id/"
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
  "created_at": "2025-06-10T19:00:01.079Z",
  "status": {
    "code": "processing",
    "sub_code": "string",
    "updated_at": "2025-06-10T19:00:01.079Z"
  },
  "metadata": {
    "additionalProp": "string"
  },
  "data": {
    "title": "string",
    "zoom": {
      "meeting_uuid": "string"
    }
  }
}
```
